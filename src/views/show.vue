<template>
     <pull-refresh :next="pullRefresh"  language="English" loadingTip="Try To Loading ｡◕ᴗ◕｡"
     :maxDistance="180">
    <div slot="list" class="show">
        <header>
            <h1>Vue Pull To Refresh Plugin</h1>
        </header>
        <article>
                <div  class="slotList">   
                    <section  class="section-one" v-if="!panel">
                        <div class="ui">
                            <h2>Panel One</h2>
                            <ripple class="ripPanel">
                                <div slot="pure" class="panel">
                                    <header>
                                        <h3>This is a Panel One</h3>
                                    </header>
                                    <div class="content">
                                        <p>Panel One</p>
                                        <ul class="form-list">
                                            <li class="form-list-item" v-for="(item, index) of message" key="index">
                                                <div class="list-item">
                                                    <span class="list-item-name">{{item.name}}</span>
                                                    <p class="item-value">{{item.value}}</p>
                                                </div>
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                            </ripple>
                        </div>
                        <div class="code" v-hljs>
                            <pre><code>{{codeOne.html}}</code></pre>
                        </div>
                    </section>
                    <section class="section-two" v-else>
                        <div class="ui">
                            <h2>Panel Two</h2>
                            <ripple class="ripPanel">
                                <div slot="pure" class="panel">
                                    <header>
                                        <h3>This is a Panel Two</h3>
                                    </header>
                                    <div class="content">
                                        <p>Panel Two</p>
                                        <ul class="form-list">
                                            <li class="form-list-item" v-for="(item, index) of message" key="index">
                                                <div class="list-item">
                                                    <span class="list-item-name">{{item.name}}</span>
                                                    <p class="item-value">{{item.value}}</p>
                                                </div>
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                            </ripple>
                        </div>
                        <div class="code" v-hljs>
                            <pre><code>{{codeTwo.html}}</code></pre>
                        </div>
                    </section>
                </div>
           <section class="section-first">
                <div class="ui">
                    <h2>Use</h2>
                    <p class="remind">
                         <span class="keypoint">
                            <img class="remind-img" src="../assets/icon/resume.svg">
                            <strong>You should restart vue after finishing install vue-usemodal</strong>
                        </span>
                         <span class="keypoint">
                            <img class="remind-img" src="../assets/icon/resume.svg">
                            <strong>next function must return promise</strong>
                        </span>
                        <span>
                            Ripple isn't necessary
                        </span>
                    </p>
                </div>
                <div class="code" v-hljs>
                    <pre><code>{{codeFirst.npm}}</code></pre>
                    <pre><code>{{codeFirst.js}}</code></pre>
                </div>
            </section>
        </article>
        <footer>
            <p>Copyright {{copyRightYear}} © by <a href="https://github.com/LDQ-first">LDQ-first</a> (◕ᴗ◕)</p>
            <p>
                demo source code in Github => 
                <a href="https://github.com/LDQ-first/vue-pulltorefresh-plugin" title="click me">
                    <img class="github-img" src="../assets/icon/github.svg" >
                </a>
            </p>
            <p>
                vue plugin source code in Github => 
                <a href="https://github.com/LDQ-first/vue-pull-to-refresh" title="click me">
                    <img class="github-img" src="../assets/icon/github.svg" >
                </a>
            </p>
        </footer>
        
    </div>
    </pull-refresh>
</template>

<script>
  /*  const pullRefresh = resolve => require(['../components/pullRefreshs.vue'], resolve)*/
    
    export default {
        data () { 
            return {
                panel: 0,
                codeFirst: {
                    npm: '',
                    js: ''
                },
                copyRightYear: '',
                isInline: true,
                codeOne: {
                    html: ''
                },
                codeTwo: {
                    html: ''
                },
                message: [
                    {name: 'name', value: 'LDQ-first'},
                    {name: 'age', value: '22'},
                    {name: 'address', value: 'address'},
                    {name: 'phone', value: '1314520'},
                ]
            }
        },
       /* components: {
            pullRefresh
        },*/
        created () {
            this.setCode()
            this.setYear()
        },
        methods: {
            pullRefresh () {
                console.log('pullRefresh')
                return new Promise((resolve, reject) => {
                    setTimeout(() => {
                        this.panel = this.panel ? 0 : 1 
                        this.message = this.panel ? [
                            {name: 'name', value: 'Vue'},
                            {name: 'age', value: '4'},
                            {name: 'address', value: "Vue's home"},
                            {name: 'phone', value: '888866662222'},
                        ] : [
                            {name: 'name', value: 'LDQ-first'},
                            {name: 'age', value: '22'},
                            {name: 'address', value: 'address'},
                            {name: 'phone', value: '1314520'},
                        ]
                        resolve()
                    }, 1200)
                })
            },
            setYear () {
                const year = new Date().getFullYear()
                if(year === 2017) {
                     this.copyRightYear = 2017
                } else {
                    this.copyRightYear = 2017 + ' - ' + year
                }
                
            },
            setCode () {
                this.codeFirst.npm =
    `
    /*-- npm --*/
    npm install --save vue-pull-to-refresh
    `
                    this.codeFirst.js = 
    `
    /*-- main.js --*/
    import Vue from 'vue'
    import VuePullToRefresh from 'vue-pull-to-refresh'
    Vue.use(VuePullToRefresh)
    `
                    this.codeOne.html = 
    ` 
    <!--html-->
     <pull-refresh :next="pullRefresh"  language="English" loadingTip="Try To Loading ｡◕ᴗ◕｡"
     :maxDistance="180">
    <div slot="list" class="show">
        . . .
    </div>
    </pull-refresh>
   
    `
                    this.codeTwo.html =
    `
    <!--html-->
     <!--html-->
     <pull-refresh :next="pullRefresh"  language="English" loadingTip="Try To Loading ｡◕ᴗ◕｡"
     :maxDistance="180">
    <div slot="list" class="show">
        . . .
    </div>
    </pull-refresh>
    
    `
                
            }

        }
     }
</script>

<style lang="scss" scoped>
    h1, h2, h3, p{
        margin: 10px 0;
    }
    section, footer {
        margin: 50px 0;
    }
    strong {
        margin: 0 20px;
    }
    .remind {
        width: 80%;
        max-width: 800px;
        margin: 20px auto;
        border: 2px solid #8BE388; 
        padding: 20px 0;
        background: #EEE;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        span {
            margin: 10px 0;
        }
        .keypoint  {
            .remind-img {
                margin: 0 20px;
                vertical-align: middle;
            }
        }
        
    } 
    .github-img {
        width: 30px;
        vertical-align: bottom;
        margin: 0 10px;
        animation: sway 2s ease-in-out infinite alternate;
        transform-origin: 50% 100%;
    }
    @keyframes sway {
        0% {
            transform: rotate(-35deg)
        }
        100% {
            transform: rotate(35deg)
        }
    }
    .code {
        width: 80%;
        max-width: 768px;
        margin: 0 auto;
    }
    .content {
        width: 100%;
        background: rgba(255, 255, 255, 0.5);
    }
    .slotList {
    }
    .form-list  {
        padding: 10px;
        .form-list-item {
            margin: 10px 0;
            .list-item {
                display: flex;
                justify-content: space-between;
                height: 40px;
                .list-item-name {
                    width: 60px;
                    margin-right: 1em;
                    display: inline-flex;
                    justify-content: flex-end;
                    align-items: center;
                }
                .list-item-value {
                    width: calc(80% - 80px)
                }
                .item-value {
                    width:  calc(80% - 80px);
                    border: 2px solid #CC99CC;
                    padding: 0.5em 2em;
                    border-radius: 2em;
                    margin: 0;
                    height: 1em;
                    line-height: 1em;
                }
            }
        }
    }
     @mixin panel {
        border: 2px solid #8BE388; 
        padding: 20px;
        background: #EEE;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        header {
            width: 100%;
            text-align: left;
        } 
        .content {
            margin: 20px 0;
        }
    }
    .section-one, .section-two {
        .ripPanel.rippleWrapper {
            width: 80%;
            max-width: 800px;
            margin: 20px auto;
        }
        .panel {
             @include panel
        }
        .br {
            width: 88px;
            height: 88px;
        }
        .des {
            margin: 0 10px;
        }
    }
    
</style>
