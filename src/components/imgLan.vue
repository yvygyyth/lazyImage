<template>
    <div class="box" ref="box">
        <img dataUrl="../src/assets/leishen.jpg" alt="" src="../assets/logo.png">
        <img dataUrl="../src/assets/leishen.jpg" alt="" src="../assets/logo.png">
        <img dataUrl="../src/assets/leishen.jpg" alt="" src="../assets/logo.png">
        <img dataUrl="../src/assets/leishen.jpg" alt="" src="../assets/logo.png">
        <img dataUrl="../src/assets/leishen.jpg" alt="" src="../assets/logo.png">
        <img dataUrl="../src/assets/leishen.jpg" alt="" src="../assets/logo.png">
        <img dataUrl="../src/assets/leishen.jpg" alt="" src="../assets/logo.png">
    </div>
</template>
<script>
export default{
    name:"imgLan",
    data(){
        return{

        }
    },
    methods:{
        deBounce(fn,time){
            let timer;
            return function(){
                clearTimeout(timer);
                timer = setTimeout(()=>{
                    fn.apply(this,arguments);
                },time)
            }   
        }, 
        lazyImage(){
            let imgArr = this.$refs.box.children;
            Array.from(imgArr).forEach(image => {
                const imgTop = image.getBoundingClientRect().top;
                console.log(image.src,image.dataUrl)
                if(imgTop-200<window.innerHeight){
                    image.setAttribute("src",image.getAttribute("dataUrl"));
                }
        });
        },
    },
    created(){
        window.addEventListener('scroll',this.deBounce(this.lazyImage,1000));
    },
}
</script>
<style>
img{
    margin-top: 20px;
}
.box{
    display: flex;
    flex-direction: column;
}
</style>