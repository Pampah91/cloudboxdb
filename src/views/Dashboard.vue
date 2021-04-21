<template>
  <div class="dashboard">
    <h1>Mon tableau de bord</h1>
  </div>

  <nav id="sidebar">
                <div class="sidebar-header">
                   <h3>Cloudbox</h3>
                </div>

                <ul class="list-unstyled components">
                    <p>Mon tableau de bord</p>
                    <li class="active">
                        <a href="#homeSubmenu" data-toggle="collapse" >Home</a>
                    </li>
                    <li>
                        <a href="#">A propos</a>
                    </li>
                    <li>
                        <a href="#">Mes avions</a>
                    </li>
                    <li>
                        <a href="#">Contact</a>
                    </li>
                </ul>

                <ul class="list-unstyled CTAs">
                    <li><a href="#" class="download">Liste des vols</a></li>
                    <li><a href="#" class="article">Rapports d'incidents</a></li>
                </ul>
            </nav>

  <div class="main">
    <div class="datablock" id="currenttime">{{heure}}</div>
    <div class="datablock" id="compte">{{planeName}}</div>
    <div class="datablock">{{planeStatus}}</div>
  </div>

  
    <div class="frames">
        <iframe class="graph" seamless frameborder="0" scrolling="no" 
        src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTfOE4BVepm36hiMbfzdpyvomHDBCgT4-wt5kap4AG8bz0pzfzKd4T0S0JQU_QjKuMrqKVysY0jf8H4/pubchart?oid=1229632621&amp;format=interactive">
        </iframe>

        <iframe class="graph" seamless frameborder="0" scrolling="no" 
        src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTfOE4BVepm36hiMbfzdpyvomHDBCgT4-wt5kap4AG8bz0pzfzKd4T0S0JQU_QjKuMrqKVysY0jf8H4/pubchart?oid=1304253821&amp;format=interactive">
        </iframe>
    </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import UserForm from '@/components/UserForm.vue'

export default {
  name: 'Dashboard',
  components: {
    
  },
  data: function(){
      return{
        heure: '',
        planeName:' Avion : POC1',
        planeStatus: 'Statut : en vol'
      }
    
  },
  created() {
    setInterval(() => {
      this.getNow();
    }, 1000)
  },
  methods:{
    getNow: function() {
      const today = new Date();;
      const time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
      const dateTime = time;
      this.heure = dateTime;
    },
  }
}


</script>

<style>
  body{
    background-color: #166088;
  }

  h1{
      color:#ddd;
      margin-left:120px;
      padding-bottom: 30px;
      text-align:center;
  }

  .main{
    margin-left: 200px;
  }

  .datablock{
    display: inline-block;
    background-color: #4a6fa5;
    width: 300px;
    height: 220px;
    margin-right: 80px;
    font-size: 220%;
    vertical-align: middle;
  }



  .frames{
    margin-left: 130px;
  }
 
  .graph{
    width: 600px;
    height: 371px;
    -ms-transform: scale(0.75);
    -moz-transform: scale(0.75);
    -o-transform: scale(0.75);
    -webkit-transform: scale(0.75);
    transform: scale(0.75);
  }



 /* Required for navbar */

 @import "https://fonts.googleapis.com/css?family=Poppins:300,400,500,600,700";

 a, a:hover, a:focus {
    color: inherit;
    text-decoration: none;
    transition: all 0.3s;
}

.navbar {
    padding: 15px 10px;
    background: #fff;
    border: none;
    border-radius: 0;
    margin-bottom: 40px;
    box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.1);
}

.navbar-btn {
    box-shadow: none;
    outline: none !important;
    border: none;
}

.line {
    width: 100%;
    height: 1px;
    border-bottom: 1px dashed #ddd;
    margin: 40px 0;
}

/* ---------------------------------------------------
    SIDEBAR STYLE
----------------------------------------------------- */

.article:hover, .download:hover{
  background: #487eb0;
}


#sidebar {
    width: 250px;
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    z-index: 999;
    background: #2f3640;
    color: #fff;
    transition: all 0.3s;
}

#sidebar.active {
    margin-left: -250px;
}


#sidebar .sidebar-header {
    padding: 20px;
    background: #487eb0;
}

#sidebar ul.components {
    padding: 20px 0;
    border-bottom: 1px solid #47748b;
}

#sidebar ul p {
    color: #fff;
    padding: 10px;
}

#sidebar ul li a {
    padding: 10px;
    font-size: 1.1em;
    display: block;
}
#sidebar ul li a:hover {
    color: #487eb0;
    background: #fff;
}

#sidebar ul li.active > a, a[aria-expanded="true"] {
    color: #fff;
    background: #6d7fcc;
}


a[data-toggle="collapse"] {
    position: relative;
}

a[aria-expanded="false"]::before, a[aria-expanded="true"]::before {
    content: '\e259';
    display: block;
    position: absolute;
    right: 20px;
    font-family: 'Glyphicons Halflings';
    font-size: 0.6em;
}
a[aria-expanded="true"]::before {
    content: '\e260';
}


ul ul a {
    font-size: 0.9em !important;
    padding-left: 30px !important;
    background: #6d7fcc;
}

ul.CTAs {
    padding: 20px;
}

ul.CTAs a {
    text-align: center;
    font-size: 0.9em !important;
    display: block;
    border-radius: 5px;
    margin-bottom: 5px;
}
a.download {
    background: #fff;
    color: #7386D5;
}
a.article, a.article:hover {
    background: #6d7fcc !important;
    color: #fff !important;
}


/* ---------------------------------------------------
    CONTENT STYLE
----------------------------------------------------- */
#content {
    width: calc(100% - 250px);
    padding: 40px;
    min-height: 100vh;
    transition: all 0.3s;
    position: absolute;
    top: 0;
    right: 0;
}
#content.active {
    width: 100%;
}


/* ---------------------------------------------------
    MEDIAQUERIES
----------------------------------------------------- */
@media (max-width: 768px) {
    #sidebar {
        margin-left: -250px;
    }
    #sidebar.active {
        margin-left: 0;
    }
    #content {
        width: 100%;
    }
    #content.active {
        width: calc(100% - 250px);
    }
    #sidebarCollapse span {
        display: none;
    }
}

</style>
