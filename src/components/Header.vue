<template>
    <header>
        <div class="logo">
            <a href="./">
                Horizon<span class="text-gradient">.</span>
            </a>
        </div>
        <div class="nav">
            <div 
                class="nav-burger-icon" 
                :class="navHandler.opened ? 'nav-opened' : 'nav-closed'"
                @click="openNavigation()"
            >
                <div class="burger-bar burger-bar-1"></div>
                <div class="burger-bar burger-bar-2"></div>
            </div>
            <div 
                class="nav-sitemap"
                :class="navHandler.opened ? 'nav-sitemap-opened' : 'nav-sitemap-closed'"
            >
                <ul>
                    <li class="nav-sitemap-title">
                        Beleggingsproducten
                    </li>
                    <li>
                        <a href="#etfs">ETF's</a>
                    </li>
                    <li>
                        <a href="#stocks">Aandelen</a>
                    </li>
                    <li>
                        <a href="#us-stocks">V.S. Aandelen</a>
                    </li>
                    <li>
                        <a href="#materials">Grondstoffen</a>
                    </li>
                </ul>
            </div>
        </div>
    </header>
    <div class="head">
        <h1>Horizon belegging screener.</h1>
        <p>Met gemak het rendement bekijken bij het beleggen in aandelen, ETF's en meer.</p>
    </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            navHandler: {
                opened: false
            },
        }
    },
    methods: {
        openNavigation: function() {
            this.navHandler.opened = !this.navHandler.opened;
        }
    }
}
</script>

<style lang="scss" scoped>
header {
    background-color: #fff;
    .logo {
        float: left;
        a:link, a:visited {
            text-decoration: none;
            color: #27332F;
            font-size: 24px;
            .text-gradient {  
                font-size: 32px;    
                background-image: var(--accent-gradient);
                background-clip: text;
                -webkit-background-clip: text;
                -webkit-text-fill-color: transparent;
                background-size: 400%;
                background-position: 0%;
            }
        }
    }
    .nav {
        float: right;
        .nav-burger-icon {
            margin-top: 16px;
            .burger-bar {
                width: 30px;
                height: 2px;
                background-color: #27332F;
                transition: 0.5s;
            }
            .burger-bar-1 {
                margin-bottom: 8px;
            }
            .burger-bar-2 {
                margin-top: 8px;
            }
        }
        .nav-opened {
            .burger-bar-1 {
                transform: translateY(5px);
            }
            .burger-bar-2 {
                transform: translateY(-5px);
            }
        }
        .nav-burger-icon:hover {
            cursor: pointer;
        }
    }
    .nav-sitemap {
        position: absolute;
        display: none;
        top: 52px;
        left: 0;
        ul {
            background-color: #fff;
            padding-bottom: 20px;
            li {
                list-style-type: none;
                width: 100vw;
                padding: 6px 0px;
                a:link, a:visited {
                    color: #27332F;
                    font-size: 24px;
                    text-decoration: none;
                }
            }
            .nav-sitemap-title {
                font-size: 24px;
                font-weight: 500;
            }
        }
    }
    .nav-sitemap-opened {
        display: block;
    }
}

header::after {
    clear: both;
    content: "";
    display: table;
}

.head {
    border-bottom: 1px solid #E3E3E3;
    h1 {
        color: #27332F;
        font-weight: 400;
    }
    p {
        color: #5f676e;
    }
}

// Viewport@Devices => Phones and Tablet
@media only screen and (max-width: 820px) {
    header {
        padding: 0 4vw;
        padding-bottom: 10px;
        .nav {
            .nav-sitemap {
                ul {
                    li {
                        padding-left: 4vw;
                    }
                }
            }
        }
    }
    .head {
        padding: 10px 4vw;
        padding-bottom: 30px;
        p {
            width: 380px;
        }
    }
}

// Viewport@Devices => Phones additional
@media only screen and (max-width: 450px) {
    .head {
        h1 {
            font-size: 27px;
        }
        p {
            font-size: 16px;
            width: 80vw;
        }
    }
}

// Viewport@Devices => Laptops
@media only screen and (min-width: 820px) and (max-width: 1440px) {
    header {
        padding: 0 2vw;
        padding-bottom: 10px;
        .nav {
            .nav-sitemap {
                ul {
                    li {
                        padding-left: 2vw;
                    }
                }
            }
        }
    }
    .head {
        padding: 10px 2vw;
        padding-bottom: 30px;
    }
}

// Viewport@Devices => +1440px (e.g. Televisions)
@media only screen and (min-width: 1440px) {
    header {
        padding: 0 1vw;
        padding-bottom: 10px;
        .nav {
            .nav-sitemap {
                ul {
                    li {
                        padding-left: 1vw;
                    }
                }
            }
        }
    }
    .head {
        padding: 10px 1vw;
        padding-bottom: 30px;
    }
}
</style>