# Learning
- System Learning
   - Set up accounts in
   
   
   
get GPS data including the positions of stop signs and traffic lights 2. Changliang generates GuidePath in Kyber-Sim (one hour work) and we train our model with Xinyu's updated Kyber-System. 3. Containerize the trained model and deploy it on Moose (Tomorrow afternoon?), which basically tests our model for static environment 4.  Waiting for other teams' ready for proving  (traffic light state ?) and heading car info. 5. Meanwhile, train model in a dynamic environment with a heading car in Webots. 

现在我们再来看一下工作目录里的“readme.txt”文件的内容：

$cat readme.txt 
<<<<<<< HEAD 
hola,world 
======= 
hello, mundo 
>>>>>>> test
“<<<<<<< HEAD“下面就是当前版本里的内容；而“=======”之下，“>>>>>>> test”之上则表示测试分支里与之对应的有冲突的容。修复冲突时我们要做的，一般就是把“ <<<<<<< HEAD”，“=======”和“ >>>>>>> test”这些东东先去掉，然后把代码改成我们想要的内容。
