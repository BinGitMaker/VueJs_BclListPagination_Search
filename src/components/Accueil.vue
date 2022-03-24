<style >
/* ensemble des cadres de listes */
.all{ 
  display:flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-inline: 10%;
  margin-block: 3%;
}

/* un cadre de liste */
.box{
  border: 2px solid #333;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  padding-block: 3%;
}

/* titre de liste */
.boxTitle{
  margin-bottom: 2rem;
  text-align: center;
}
</style>

<template>
<div class="all">
  <div class="box box-1" :style="box">
    <h1 class="boxTitle">Liste de nos Sites1 </h1>
      <div>
        <Liste :my-prop-list="message" :my-url-list="items1"/>
      </div>
  </div>
  <div class="box box-2" :style="box">
    <h1 class="boxTitle">Liste de nos Sites2 </h1>
      <div>
        <Liste :my-prop-list="message" :my-url-list="items2"/>
      </div>
  </div>
  <div class="box box-3" :style="box">
    <h1 class="boxTitle">Liste de nos Sites3 </h1>
      <div>
        <Liste :my-prop-list="message" :my-url-list="items3"/>
      </div>
  </div>
</div>
</template>
<script>

import Liste from './Liste.vue'

export default {
  name: 'Accueil',
  components: {
    Liste, // composant Liste.vue
  },  
  data(){
    return {
      message: 'Liste',
      width: 30, // affichage Css de la width
      margin: 3, // affichage Css des margin
      
      // Parent: declare les items et les ecrit en html
      // Enfants: initie le template et le defini en props
      items1: [
            { label: "As de coeur", 
            url: 'https://deckofcardsapi.com/static/img/6H.png', 
            lgTxt: "Lorem 1 ipsum dolor sit, amet consectetur adipisicing elit. Numquam consequuntur magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de trèfle", 
            url: 'https://deckofcardsapi.com/static/img/aceDiamonds.png', 
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de carreau", 
            url: 'https://deckofcardsapi.com/static/img/7C.png', 
            lgTxt: "Lorem 2 ipsum dolor sit, amet consectetur adipisicing elit. Numquam consequuntur magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de coeur", 
            url: 'https://deckofcardsapi.com/static/img/6H.png', 
            lgTxt: " magnam 3 reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de trèfle", 
            url: 'https://deckofcardsapi.com/static/img/aceDiamonds.png', 
            lgTxt: "Lorem 4 ipsum dolor sit, amet consectetur adipisicing elit. Numquam consequuntur magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de carreau", 
            url: 'https://deckofcardsapi.com/static/img/7C.png', 
            lgTxt: " magnam 5 reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de coeur", 
            url: 'https://deckofcardsapi.com/static/img/6H.png', 
            lgTxt: "Lorem 6 ipsum dolor sit, amet consectetur adipisicing elit. Numquam consequuntur magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de trèfle", 
            url: 'https://deckofcardsapi.com/static/img/aceDiamonds.png',
            lgTxt: " magnam 7 reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de carreau", 
            url: 'https://deckofcardsapi.com/static/img/7C.png',
            lgTxt: "Lorem 8 ipsum dolor sit, amet consectetur adipisicing elit. Numquam consequuntur magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de coeur", 
            url: 'https://deckofcardsapi.com/static/img/6H.png',
            lgTxt: " magnam 9 reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de trèfle", 
            url: 'https://deckofcardsapi.com/static/img/aceDiamonds.png',
            lgTxt: " magnam 10 reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de carreau", 
            url: 'https://deckofcardsapi.com/static/img/7C.png',
            lgTxt: "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Numquam consequuntur magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de coeur", 
            url: 'https://deckofcardsapi.com/static/img/6H.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de trèfle", 
            url: 'https://deckofcardsapi.com/static/img/aceDiamonds.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de carreau", 
            url: 'https://deckofcardsapi.com/static/img/7C.png',
            lgTxt: "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Numquam consequuntur magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de coeur", 
            url: 'https://deckofcardsapi.com/static/img/6H.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de trèfle", 
            url: 'https://deckofcardsapi.com/static/img/aceDiamonds.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de carreau", 
            url: 'https://deckofcardsapi.com/static/img/7C.png',
            lgTxt: "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Numquam consequuntur magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de coeur", 
            url: 'https://deckofcardsapi.com/static/img/6H.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "As de trèfle", 
            url: 'https://deckofcardsapi.com/static/img/aceDiamonds.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
        ], 
      items2: [
            { label: "chevron", 
            url: 'https://deckofcardsapi.com/static/img/67HJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "bâton rompu", 
            url: 'https://deckofcardsapi.com/static/img/stainWater.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "pointe de hongrie", 
            url: 'https://deckofcardsapi.com/static/img/9CD.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "chevron", 
            url: 'https://deckofcardsapi.com/static/img/67HJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "bâton rompu", 
            url: 'https://deckofcardsapi.com/static/img/stainWater.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "pointe de hongrie", 
            url: 'https://deckofcardsapi.com/static/img/9CD.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "chevron", 
            url: 'https://deckofcardsapi.com/static/img/67HJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "bâton rompu", 
            url: 'https://deckofcardsapi.com/static/img/stainWater.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "pointe de hongrie", 
            url: 'https://deckofcardsapi.com/static/img/9CD.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "chevron", 
            url: 'https://deckofcardsapi.com/static/img/67HJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "bâton rompu", 
            url: 'https://deckofcardsapi.com/static/img/stainWater.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "pointe de hongrie", 
            url: 'https://deckofcardsapi.com/static/img/9CD.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "chevron", 
            url: 'https://deckofcardsapi.com/static/img/67HJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "bâton rompu", 
            url: 'https://deckofcardsapi.com/static/img/stainWater.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "pointe de hongrie", 
            url: 'https://deckofcardsapi.com/static/img/9CD.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "chevron", 
            url: 'https://deckofcardsapi.com/static/img/67HJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "bâton rompu", 
            url: 'https://deckofcardsapi.com/static/img/stainWater.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "pointe de hongrie", 
            url: 'https://deckofcardsapi.com/static/img/9CD.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "chevron", 
            url: 'https://deckofcardsapi.com/static/img/67HJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "bâton rompu", 
            url: 'https://deckofcardsapi.com/static/img/stainWater.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
        ],
      items3: [
            { label: "Yoda", 
            url: 'https://deckofcardsapi.com/static/img/5GJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "Vador", 
            url: 'https://deckofcardsapi.com/static/img/goldenStone.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "Solo", 
            url: 'https://deckofcardsapi.com/static/img/25E.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "Yoda", 
            url: 'https://deckofcardsapi.com/static/img/5GJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "Vador", 
            url: 'https://deckofcardsapi.com/static/img/goldenStone.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "Solo", 
            url: 'https://deckofcardsapi.com/static/img/25E.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "Yoda", 
            url: 'https://deckofcardsapi.com/static/img/5GJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "Vador", 
            url: 'https://deckofcardsapi.com/static/img/goldenStone.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."},
            { label: "Solo", 
            url: 'https://deckofcardsapi.com/static/img/25E.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Yoda", 
            url: 'https://deckofcardsapi.com/static/img/5GJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Vador", 
            url: 'https://deckofcardsapi.com/static/img/goldenStone.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Solo", 
            url: 'https://deckofcardsapi.com/static/img/25E.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Yoda", 
            url: 'https://deckofcardsapi.com/static/img/5GJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Vador", 
            url: 'https://deckofcardsapi.com/static/img/goldenStone.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Solo", 
            url: 'https://deckofcardsapi.com/static/img/25E.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Yoda", 
            url: 'https://deckofcardsapi.com/static/img/5GJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Vador", 
            url: 'https://deckofcardsapi.com/static/img/goldenStone.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Solo", 
            url: 'https://deckofcardsapi.com/static/img/25E.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Yoda", 
            url: 'https://deckofcardsapi.com/static/img/5GJ.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Vador", 
            url: 'https://deckofcardsapi.com/static/img/goldenStone.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
            { label: "Solo", 
            url: 'https://deckofcardsapi.com/static/img/25E.png',
            lgTxt: " magnam reiciendis perspiciatis iusto. Adipisci modi, voluptate corporis aliquid vel nemo incidunt eos repudiandae blanditiis. Neque perferendis doloribus nisi quam."
            },
        ],
    }
  },
  computed: {
    box: function(){
      return{
        width: this.width + "rem",
        margin: this.margin + "rem",
      }
    }
  }

}

</script>



