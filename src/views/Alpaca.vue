<template>
    <div>
        <h1 class="heading">Alpaca image generator</h1>

        <div class="alpaca-container row">
            <div class="col border">
                <div class="img-container" id="divId">
                    <div class="all-img">
                        <div class="author">
                            <a href="https://www.linkedin.com/in/dharmendra-kumar-a588a4119/">By Dharam</a>
                        </div>
                        <div class="background">
                            <img ref="backgroundImg" src="../assets/alpaca/backgrounds/blue50.png" alt="">
                        </div>
                        <div class="ears">
                            <img ref="ears" src="../assets/alpaca/ears/default.png" alt="">
                        </div>

                        <div class="hair">
                            <img ref="hair" src="../assets/alpaca/hair/default.png" alt="">
                        </div>
                        <div class="eyes">
                            <img ref="eyes" src="../assets/alpaca/eyes/default.png" alt="">
                        </div>
                        <div class="leg">
                            <img ref="leg" src="../assets/alpaca/leg/default.png" alt="">
                        </div>
                        <div class="neck">
                            <img ref="neck" src="../assets/alpaca/neck/default.png" alt="">
                        </div>
                        <div class="nose">
                            <img ref="nose" src="../assets/alpaca/nose.png" alt="">
                        </div>
                        <div class="mouth">
                            <img ref="mouth" src="../assets/alpaca/mouth/default.png" alt="">
                        </div>
                        <div class="eyes">
                            <img ref="eyes" src="../assets/alpaca/eyes/default.png" alt="">
                        </div>
                        <div class="accessories">
                            <img ref="accessories" src="../assets/alpaca/accessories/headphone.png" alt="">
                        </div>

                    </div>
                </div>
                <div class="custom-btn border">
                    <button class="btn btn-random" @click.prevent="randomImageGenerator">Random</button>
                    <button class="btn btn-download" @click.prevent="downloadImage()">Download</button>
                </div>
            </div>
            <div class="col border">
                <div>
                    <h2>ACCESSORIZE THE ALPACA'S</h2>
                    <div class="accessories-btn">
                        <NormalButton v-for="(item, index) in accBtnNameList" :key="index"
                            :class="{ active: activeAccIndex === index }" :btnName="item.name" :itemList=item.itemList
                            isAccessories=true :index="index" @onclickData="activeItemData"></NormalButton>
                    </div>
                </div>
                <div>
                    <h2>STYLE</h2>
                    <div class="accessories-item-btn">
                        <NormalButton v-for="(item, index) in activeAcc" :key="index"
                            :class="{ active: activeItemIndex === index }" :btnName="item.name" isAccessories=false
                            :index="index" @activeItem="activeItem"></NormalButton>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import NormalButton from '../components/NormalButton.vue';
export default {
    data() {
        return {
            btnName: "new ",
            activeAccIndex: 0,
            activeItemIndex: 0,
            activeItemName: "Accessories",
            accBtnNameList: [{
                name: "Accessories",
                itemList: [
                    {
                        name: "default",
                        src: "./src/assets/alpaca/accessories/headphone.png"
                    },
                    {
                        name: "earings",
                        // src: require(`@/assets/images/business/`)
                        // src: "./src/assets/alpaca/accessories/earings.png"
                    },
                    {
                        name: "flower",
                        src: "./src/assets/alpaca/accessories/flower.png"
                    },
                    {
                        name: "glasses",
                        src: "./src/assets/alpaca/accessories//glasses.png"
                    },

                ]
            },
            {
                name: "Backgrounds",
                itemList: [
                    {
                        name: "default",
                        src: "./src/assets/alpaca/backgrounds/blue50.png"
                    },
                    {
                        name: "blue60",
                        src: "./src/assets/alpaca/backgrounds/blue60.png"
                    },
                    {
                        name: "blue70",
                        src: "./src/assets/alpaca/backgrounds/blue70.png"
                    },
                    {
                        name: "darkblue30",
                        src: "./src/assets/alpaca/backgrounds/darkblue30.png"
                    },
                    {
                        name: "darkblue50",
                        src: "./src/assets/alpaca/backgrounds/darkblue50.png"
                    },
                    {
                        name: "darkblue70",
                        src: "./src/assets/alpaca/backgrounds/darkblue70.png"
                    },
                    {
                        name: "green50",
                        src: "./src/assets/alpaca/backgrounds/green50.png"
                    },
                    {
                        name: "green60",
                        src: "./src/assets/alpaca/backgrounds/green60.png"
                    },
                    {
                        name: "green70",
                        src: "./src/assets/alpaca/backgrounds/green70.png"
                    },
                    {
                        name: "grey40",
                        src: "./src/assets/alpaca/backgrounds/grey40.png"
                    },
                    {
                        name: "grey70",
                        src: "./src/assets/alpaca/backgrounds/grey70.png"
                    },
                    {
                        name: "grey80",
                        src: "./src/assets/alpaca/backgrounds/grey80.png"
                    },

                    {
                        name: "red50",
                        src: "./src/assets/alpaca/backgrounds/red50.png"
                    },
                    {
                        name: "red60",
                        src: "./src/assets/alpaca/backgrounds/red60.png"
                    },
                    {
                        name: "red70",
                        src: "./src/assets/alpaca/backgrounds/red70.png"
                    },
                    {
                        name: "yellow50",
                        src: "./src/assets/alpaca/backgrounds/yellow50.png"
                    },
                    {
                        name: "yellow60",
                        src: "./src/assets/alpaca/backgrounds/yellow60.png"
                    },
                    {
                        name: "yellow70",
                        src: "./src/assets/alpaca/backgrounds/yellow70.png"
                    },


                ]
            },
            {
                name: "Ears",
                itemList: [
                    {
                        name: "default",
                        src: "./src/assets/alpaca/ears/default.png"
                    },
                    {
                        name: "tilt-backward",
                        src: "./src/assets/alpaca/ears/tilt-backward.png"
                    },
                    {
                        name: "tilt-forward",
                        src: "./src/assets/alpaca/ears/tilt-forward.png"
                    },
                ]
            },
            {
                name: "Eyes",
                itemList: [
                    {
                        name: "default",
                        src: "./src/assets/alpaca/eyes/default.png"
                    },
                    {
                        name: "angry",
                        src: "./src/assets/alpaca/eyes/angry.png"
                    },
                    {
                        name: "naughty",
                        src: "./src/assets/alpaca/eyes/naughty.png"
                    },
                    {
                        name: "panda",
                        src: "./src/assets/alpaca/eyes/panda.png"
                    },
                    {
                        name: "smart",
                        src: "./src/assets/alpaca/eyes/smart.png"
                    },
                    {
                        name: "star",
                        src: "./src/assets/alpaca/eyes/star.png"
                    },
                ]
            },
            {
                name: "Hair",
                itemList: [
                    {
                        name: "default",
                        src: "./src/assets/alpaca/hair/default.png"
                    },
                    {
                        name: "bang",
                        src: "./src/assets/alpaca/hair/bang.png"
                    },
                    {
                        name: "curls",
                        src: "./src/assets/alpaca/hair/curls.png"
                    },
                    {
                        name: "elegant",
                        src: "./src/assets/alpaca/hair/elegant.png"
                    },
                    {
                        name: "fancy",
                        src: "./src/assets/alpaca/hair/fancy.png"
                    },
                    {
                        name: "quiff",
                        src: "./src/assets/alpaca/hair/quiff.png"
                    },
                    {
                        name: "short",
                        src: "./src/assets/alpaca/hair/short.png"
                    },

                ]
            },
            {
                name: "Leg",
                itemList: [
                    {
                        name: "default",
                        src: "./src/assets/alpaca/leg/default.png"
                    },
                    {
                        name: "bubble-tea",
                        src: "./src/assets/alpaca/leg/bubble-tea.png"
                    },
                    {
                        name: "cookie",
                        src: "./src/assets/alpaca/leg/cookie.png"
                    },
                    {
                        name: "game-console",
                        src: "./src/assets/alpaca/leg/game-console.png"
                    },
                    {
                        name: "tilt-backward",
                        src: "./src/assets/alpaca/leg/tilt-backward.png"
                    },
                    {
                        name: "tilt-forward",
                        src: "./src/assets/alpaca/leg/tilt-forward.png"
                    },


                ]
            },
            {
                name: "Mouth",
                itemList: [
                    {
                        name: "default",
                        src: "./src/assets/alpaca/mouth/default.png"
                    },
                    {
                        name: "astonished",
                        src: "./src/assets/alpaca/mouth/astonished.png"
                    },
                    {
                        name: "eating",
                        src: "./src/assets/alpaca/mouth/eating.png"
                    },
                    {
                        name: "laugh",
                        src: "./src/assets/alpaca/mouth/laugh.png"
                    },
                    {
                        name: "tongue",
                        src: "./src/assets/alpaca/mouth/tongue.png"
                    },

                ]
            },
            {
                name: "Neck",
                itemList: [
                    {
                        name: "default",
                        src: "./src/assets/alpaca/neck/default.png"
                    },
                    {
                        name: "bend-backward",
                        src: "./src/assets/alpaca/neck/bend-backward.png"
                    },
                    {
                        name: "bend-forward",
                        src: "./src/assets/alpaca/neck/bend-forward.png"
                    },
                    {
                        name: "thick",
                        src: "./src/assets/alpaca/neck/thick.png"
                    },
                ]
            },
            ],
            activeAcc: [],
            randomItemData: []

        }
    },
    components: {
        NormalButton
    },
    mounted() {
        this.activeAcc = this.accBtnNameList[0].itemList;
    },
    methods: {
        downloadImage() {
            html2canvas( document.getElementById( "divId" ) ).then( function ( canvas ) {
                var anchorTag = document.createElement( "a" );
                anchorTag.download = "Alpaca.jpg";
                anchorTag.href = canvas.toDataURL();
                anchorTag.target = '_blank';
                anchorTag.click();
            } );
        },


        randomImageGenerator() {
            let totalAccessories = 0;
            let activeItemLength = []
            for ( const item of this.accBtnNameList ) {
                activeItemLength.push( item.itemList.length );
                totalAccessories++;
            }
            for ( let i = 0; i < totalAccessories; i++ ) {
                let theRandomNumber = Math.floor( Math.random() * activeItemLength[i] );
                switch ( i ) {
                    case 0:
                        this.$refs.accessories.src = `${this.accBtnNameList[i].itemList[theRandomNumber].src}`;
                        break;
                    case 1:
                        this.$refs.backgroundImg.src = `${this.accBtnNameList[i].itemList[theRandomNumber].src}`
                        break;
                    case 2:
                        this.$refs.ears.src = `${this.accBtnNameList[i].itemList[theRandomNumber].src}`
                        break;
                    case 3:
                        this.$refs.eyes.src = `${this.accBtnNameList[i].itemList[theRandomNumber].src}`
                        break;
                    case 4:
                        this.$refs.hair.src = `${this.accBtnNameList[i].itemList[theRandomNumber].src}`
                        break;
                    case 5:
                        this.$refs.leg.src = `${this.accBtnNameList[i].itemList[theRandomNumber].src}`
                        break;
                    case 6:
                        this.$refs.mouth.src = `${this.accBtnNameList[i].itemList[theRandomNumber].src}`
                        break;
                    case 7:
                        this.$refs.neck.src = `${this.accBtnNameList[i].itemList[theRandomNumber].src}`
                        break;
                    default:
                        break;
                }

            }
        },
        activeItemData( item ) {
            this.activeAccIndex = item.index;;
            this.activeAcc = item.item;
            this.activeItemName = item.itemName;
            this.activeItemIndex = 0;
        },
        activeItem( index ) {
            this.activeItemIndex = index;

            switch ( this.activeItemName ) {
                case "Accessories":
                    this.$refs.accessories.src = `${this.activeAcc[this.activeItemIndex].src}`

                    break;
                case "Backgrounds":
                    this.$refs.backgroundImg.src = `${this.activeAcc[this.activeItemIndex].src}`
                    break;
                case "Ears":
                    this.$refs.ears.src = `${this.activeAcc[this.activeItemIndex].src}`

                    break;
                case "Eyes":
                    this.$refs.eyes.src = `${this.activeAcc[this.activeItemIndex].src}`

                    break;
                case "Hair":
                    this.$refs.hair.src = `${this.activeAcc[this.activeItemIndex].src}`

                    break;
                case "Leg":
                    this.$refs.leg.src = `${this.activeAcc[this.activeItemIndex].src}`

                    break;
                case "Mouth":
                    this.$refs.mouth.src = `${this.activeAcc[this.activeItemIndex].src}`

                    break;
                case "Neck":
                    this.$refs.neck.src = `${this.activeAcc[this.activeItemIndex].src}`

                    break;

                default:
                    break;
            }
        }
    },

}
</script>

<style  scoped>
.heading {
    max-width: 850px;
    margin: auto;
    padding-left: 1.5rem;
    font-size: 35px;
    text-transform: uppercase;
    margin-top: 1rem;
}

h2,
h1 {
    color: #2663be;
    margin: 1rem 0.8rem;
}

.alpaca-container {
    max-width: 850px;
    margin: auto;
}

.img-container {
    position: relative;
    width: 380px;
    height: 380px;
    margin: auto;
}

.custom-btn {
    max-width: 380px;
    margin: auto;
}

.all-img {
    background-repeat: no-repeat;
    max-width: inherit;
    height: inherit;

}

.background {
    height: inherit;
}

.all-img .background img {
    width: 100%;
    object-fit: cover !important;
}

.all-img img {
    width: 100%;
}

.all-img>* {
    position: absolute;
}

.author {
    right: 15px;
    top: 15px;
    z-index: 999;
}

.author a {
    text-decoration: none;
    color: #ffffff50;

}

.col {
    padding: .8rem;
}

.custom-btn {
    display: flex;
    justify-content: center;
    gap: .8rem;
    padding-top: .8rem;
}

.custom-btn .btn {
    flex: 1 1 100%;
    padding: 1rem 2rem;
    background-color: #5596F6;
    border: none;
    font-size: 1rem;
    font-weight: bold;
    color: white;
    transition: all .3s;
}

.custom-btn .btn:active {

    background-color: #2663be;
    color: white;
}

@media only screen and (min-width:620px) {
    .row {
        display: flex;
    }

    .col {
        flex: 1 1 100%;
    }
}</style>