# 图片懒加载

首先我们需要先获取图片列表

const images=document.querySelectorAll('img')

然后我们获取图片的数量

const length=images.length

随后我们开始写监听函数

const lazyImgFun=()=>{

​		const count=0

​		return (

​					function(){

​							const defineIndexArr=[]

​							images.forEach((img,index)=>{

​								const rect=img.getBoundingClientRect()

​								if(rect.top<window.innerHeight){

​										img.src=img.dataset.src

​										defineIndexArr.push(index)

​										count++

​								}

​							 	if(count>=length){

​										document.removeEventListener('scroll',lazyImgFun)

​								}

​							})		

​				}

​		)()

}

最后监听即可

document.addEventListener('scroll',lazyImgFun)