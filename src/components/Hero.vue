<style scoped>
/*HERO*/
.hero {
    position: relative;
    z-index: 0;
}

.hero .overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    content: '';
    width: 100%;
    background: #000000;
    z-index: -1;
    opacity: .3;
}

.hero .text {
    color: rgba(255, 255, 255, .9);
}

.hero .text h2 {
    color: #fff;
    font-size: 40px;
    margin-bottom: 0;
    font-weight: 600;
    line-height: 1;
    text-transform: uppercase;
}

.hero .text h2 span {
    font-weight: 600;
    color: #448ef6;
}
</style>