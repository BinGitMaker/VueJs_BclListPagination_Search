<style >

/* .urlText{
    overflow-wrap: anywhere;
    margin-right : 10%;
    text-align: start;
    text-decoration: none;
} */

.containResult{
    margin-top: 1rem;
}

.liste{
    list-style-type: none;
    padding-inline-start: 0;
    margin-top: 1rem;

}
/* container du titre du lien */
.labelUrlContainer{
    text-align: start;
    padding-inline-start: 15%;
    
}
/* titre du lien */
.labelUrl{
    color: black;
    font-weight: bold;
    font-size:x-large;
}

/* container du lgText */
.lgTextStyle{
    padding-inline: 10%;
    text-align: start;
}

/* texte cliquable pour afficher/masquer le lgText*/
.lien {
    color:blue;
    text-decoration: underline;
    margin-bottom: 1.5rem;
    text-align: end;
    padding-inline-end: 15%;
}

/* boutons back/next */
.btnContainer{
    position: relative;
    margin: 2rem;
}

/* style commun aux 2 boutons */
.btn2gether{
    position: absolute;
    bottom: 1rem;
}

/* style next only */
.btnIncrease{
    left: 1rem;
}

/* style back only */
.btnReduce{
    right: 1rem;
}

</style>

<template>

<div>
    <form v-on:submit.prevent="onSubmit">
            <input id="searchBar" type="text" v-model="searchText" class="form-control">
            <button class="btn">Recherche</button>
                <!-- si la variable booleen showEmptyLinkTxt est false (la variable est initialisé à false)
                alors renvoi la methode Html sorryTxt qui affiche le message "desolé on n'a rien touvé"-->
                <div class="containResult">
                    <p v-if="showEmptyLinkTxt" v-html="sorryTxt()"></p>
                </div>
                
             <ul class="liste" >
                 <!-- Boucle sur les liens (item) de la méthodes [linkFilter] qui retourne des liens triés à afficher selon la recherche (searchText)-->
               <template v-for="item in linkFilter" :key="item">
                   <li>
                       
                    <!--  affiche la methods [hideUrl] ayant lien(item) pour valeur
                    donc ca affiche les liens avec label, url et descriptif sous le format Html instancié dans la methode-->
                <p v-html="hideUrl(item)"></p>
                <!-- l'affichage de show (initialisé a false) est false (! note l'inverse de false), donc 
                    si le descriptif est caché, alors j'affiche le lien "en lire plus" -->
                    <div v-if="!show"><!-- false(!) de false donc true/ donc visible -->
                        <p class="lien" @click="show = !show">en lire plus</p>
                    </div><!-- show est visible, mais initialisé sans ! il faut lire :
                    // visible = inverse de visible, donc >>> le texte est caché -->

                    <!-- l'affichage de show (initialisé a false) est true, donc 
                    si le descriptif est visible, alors j'affiche le lien "masquer" -->
                    <div v-if="show"><!-- false/caché -->
                        <p class="lien" @click="show = !show">masquer</p>
                    </div> <!-- caché = inverse de caché, donc >>> le texte est visible -->
            </li> 
                </template> 
            </ul> 
    </form>


    <div class="container btnContainer">
        <!-- on peut diminuer tant que l'index de page n'est pas inferieur à 1 -->
        <button class="btn btn2gether btnIncrease" v-if="!page < 1" v-on:click="diminue"> back </button>
        <!-- on peut augmenter l'index de page tant qu'il n'est pas superieur au nombre total de pages-->
        <button class="btn btn2gether btnReduce" v-if="page < pageNb" v-on:click="augmente"> next </button>
        <!-- comme la 1ere position d'un index est de 0, on doit +1 chaque page et nb de page pour afficher page 1/4 et non 0/3-->
        <p>{{ page + 1 }}/{{ pageNb + 1 }}</p>
        
    </div>
    
</div>

</template>

<script>

export default {
   name: 'Liste',
    data(){
        return{
            pageNb: 3, //nb de page total
            page: 0, // index de la liste à partir de laquelle je demarre
            linkNb: 5, // nb d'elements à afficher par liste
            maxChar: 50, // nb max de caracteres à afficher en texte court
            show: false, // affichage du long/court texte
            message: 'en lire plus', // texte qui s'affiche sur le lien cliquable
            searchText: 'search', // texte qui s'initialisation de la page dans le champ de recherche
            showEmptyLinkTxt: false, // affichage ou non d'un texte "Il n'y a pas de resultat"
        }
    },
    props: {
        myPropList:{ 
            type: String,
            default: () => ''
        },
        myUrlList:{ // tableau regroupant tous les liens existants dans la page
            type: Array,
            dafaut: () => []
        },
        myLgTxtList:{ // tableau des descriptifs
            type: String,
            default: () => ''
        }
    },
    computed: {
        // OPTION 1: je boucle pour afficher toutes les pommes rouges que je trouve et je m'arrete quand j'en ai trouvé 5.
         /*linkFilter: function() {
            var lienAafficher = [];
            var premierLien = (this.page) * 5
            var dernierLien = (this.page + 1) * 5
            console.log(premierLien, dernierLien)
            
        for (let i = premierLien ; i < this.myUrlList.length ; i++) {
            // lienAafficher est vide, mais se rempli avec .push en bouclant la liste de i=0 à i=5
            
            /* console.log("test",this.myUrlList[i]) */
            /*if ((this.myUrlList[i].label.match(this.searchText)) || (this.myUrlList[i].url.match(this.searchText)) || (this.myUrlList[i].lgTxt.match(this.searchText))){
                lienAafficher.push(this.myUrlList[i])
            }
            if (lienAafficher.length == 5){
                break
            }

        } */
       /* console.log(lienAafficher) */
        /*return lienAafficher
            
        },*/

        // OPTION2 : je vais chercher toutes les pommes rouges, et je ne prend que les 5 premieres.
        linkFilter: function() {
            var lienAafficher = []; //c'est mon tableau vide qui attends de recevoir mes 5 Url/lien
            var searchLink = []; // c'est mon second tableau vide qui attend de recevoir tous les Url/liens correspondants a ma recherche searchText
            var premierLien = (this.page) * 5 // le premier index à afficher suivant le numero de page - sachant qu'on souhaite 5 liens par page
            var dernierLien = (this.page + 1) * 5 // le dernier index à afficher suivant le numero de page - sachant qu'on souhaite 5 liens par page
            

            //si ma recherche affiche le string 'search' 
            // affiche la liste totale de mes liens 
            if (this.searchText == 'search'){
                // Boucle sur tout mon tableau de liens [myUrlList.length]
                for (let a = 0 ; a < this.myUrlList.length ; a++) {
                    // si la valeur de l'index[a] de mon dernier lien [dernierLien], est superieure à la longueur de mon tableau [.length] de tous les liens [myUrlList], 
                    // alors l'index [a] de mon dernier lien [dernierLien] correspondra à la longueur de mon tableau de tous les liens [myUrlList.length].
                    if (dernierLien > this.myUrlList.length){
                    dernierLien = myUrlList.length
                     } 
                }
                // Boucle sur tout mon tableau de liens [myUrlList] (en fonction de ma recherche searchText)
                for (let a = premierLien ; a < dernierLien ; a++){
                // rempli (push) mon tableau vide de liens à afficher [lienAafficher] 
                    lienAafficher.push(this.myUrlList[a])
                    
                    // quand j'affiche la liste totale de mes liens
                    // le nombre de max de liens par page doit etre de 5
                    this.pageNb = Math.floor(this.myUrlList.length / 5)
                    }
                    // affiche les liens triés (par affichage de 5)
                    return lienAafficher

            } else {

                // Boucle sur tout mon tableau de liens [myUrlList.length]
                for (let i = 0 ; i < this.myUrlList.length ; i++) {
                    // si mes liens(label/url/descriptif) matchent avec ma recherche [searchText]
                    if ((this.myUrlList[i].label.match(this.searchText)) || (this.myUrlList[i].url.match(this.searchText)) || (this.myUrlList[i].lgTxt.match(this.searchText)))
                    {
                    // alors mon tableau vide [searchLink] par la recherche [searchText] se rempli (avec push) 
                    // des liens recherchés dans la liste de base [myUrlList]
                    searchLink.push(this.myUrlList[i])
                    } 
                // mon nombre de pages totale [pageNb] doit correspondre à la longueur totale de mon tableau de tous les liens déja triés [searchLink.length] 
                // selon la recherche [searchText] et sur un max(floor) de 5 liens par affichage.
                this.pageNb = Math.floor(searchLink.length / 5)
                console.log(searchLink)
                }
                // si la longueur du tableau des liens est nulle 
                
                if (searchLink.length == 0){
                    // alors le booleen qui conditionne l'affichage de la method "sorryTxt" est true (donc false car initialisée a false)
                    this.showEmptyLinkTxt = true
                } else {
                    // sinon le booleen qui conditionne l'affichage de la method "sorryTxt" est false (donc true )
                    this.showEmptyLinkTxt = false
                }

                // si la valeur de l'index[i] de mon dernier lien trié [dernierLien], est superieure à la longueur de mon tableau [.length] de tous les liens recherchés [searchLink], 
                    // alors l'index [i] de mon dernier lien [dernierLien] correspondra à la longueur de mon tableau de recherche de tous les liens [searchLink.length].
                    if (dernierLien > searchLink.length){
                    dernierLien = searchLink.length
                     }
                // Boucle sur tout mon tableau de liens triés [searchLink] (en fonction de ma recherche searchText)
                for (let j = premierLien ; j < dernierLien ; j++){
                // rempli (push) mon tableau vide de liens à afficher [lienAafficher] 
                    lienAafficher.push(searchLink[j])
                    }
                    console.log(lienAafficher)
                    // affiche les liens triés (par affichage de 5)
                    return lienAafficher
            /* return searchLink */

                }
            
        },
        
        showedTxt: function(){
                 if (this.lgTxt.length > this.maxChar){
                return this.lgTxt.slice(0, this.maxChar) 
            }
            return lienAafficher.length == 5
        },
         /* filteredList(){
             console.log(this.searchText)
            var search = this.searchText
            return this.myUrlList.filter( function(item) {
                return item.label.match(search) || item.lgTxt.match(search)
            }) 
        },  */
        
    },

    methods: {
        
        lienAafficher : function(item){
            if (this.searchText == true)
            return (this.myUrlList[i].label.match(this.searchText))
        },
            // hideUrl est une metodes qui agi sur les liens (items)
        hideUrl : function(item) {
            /* console.log(item) */
            // si le descriptif(lgTxt) reduit ne doit pas etre affiché (show à false)
            if (this.show == false) {
            // alors on affiche le lgTxt coupé (slice) à 50 char (paramDepart: de l'indice zero, paramFin: à l'indice de maxChar) 
                return '<div class="labelUrlContainer"><a class="labelUrl" href="'+item.url+'">'+ item.label +'</a></div>'+'<div class="lgTextStyle" ><a>'+ item.lgTxt.slice(0, this.maxChar) +'</a></div>'
            // sinon (si le descriptif peut etre affiché en entier)
            } else {
            // alors affiche lgTxt (soit le texte entier)
                return '<div class="labelUrlContainer"><a class="labelUrl" href="'+item.url+'">'+ item.label +'</a></div>'+'<div class="lgTextStyle"><a>'+ item.lgTxt +'</a></div>'
            }
                
            /* console.log(item) */
        },
            // est une methods sui retourne un message au format Html
        sorryTxt : function(){
                return '<p> Désolé! il n\'y a pas de resultat pour "'+ this.searchText +'"</p>'    
        },

        // la methods augmente
        augmente : function(){
            // incrémente l'index de la page
            this.page++;
        },
        // la methods diminue
        diminue : function(){
            // décrémente l'index de la page
            this.page--;
        },
    },
    

}
</script>