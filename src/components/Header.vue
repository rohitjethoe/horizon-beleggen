<template>
    <header>
        <div class="logo">
            <a href="./">
                Horizon<span class="text-gradient">.</span>
            </a>
        </div>
        <div class="nav">
            
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
        }
    }
    .head {
        padding: 10px 1vw;
        padding-bottom: 30px;
    }
}
</style>