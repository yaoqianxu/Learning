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


然再把改好的“readme.txt”用“git add”添加到暂存区中，最后再用“git commit”提交到本地仓库中，这个冲突（conflict）就算解决了：

$git add readme.txt 
$git commit -m "fix conflict" 
[master ebe2f18] fix conflict 
这里看起来比较怪异的地方是Git解决了冲突的办法：怎么用“git add”添加到暂存区去，“git add”不是用来未暂存文件的吧，怎么又来解决冲突了。不过我想如果你仔细读过上一篇文章的话就不难理解，因为Git是一个“snapshot”存储系统，所有新增加的内容都是直接存储的，而不是和老版本作一个比较后存储新旧版本间的差异。

Git里面合并两个版本之间的同一文件，如果两者间内容相同则不作处理，两者间内容不同但是可以合并则产生一个新的blob对象，两者间内容不同但是合并时产生了冲突，那么我们解决了冲突后要把文件“git add”到暂存区中再“git commit”提交到本地仓库即可，这就和前面一样产生一个新的blob对象。

假设我们对合并的结果不满意，可以用下面的命令来撤消前面的合并：

$git reset --hard HEAD^ 
HEAD is now at 050d890 master branch modified 
从git reset（2）命令的输出结果可以看到，主分支已经回到了合并前的状态了。

我们再用下面的命令看一下“readme.txt”文件，确认一下文件改回来没有：

$cat readme.txt 
hola,world 
小结

由于Git采用了“SHA1哈希串值内容寻值”、“快照存储（snapshot）”等方法, Git中创建分支代价是很小的速度很快；也这是因为如此，它处理合并冲突的方法与众不同。

在这里我想起了“C语言就是汇编（计算机硬件）的一个马甲”这句话，其实Git也就是底层文件系统的一个马甲，只不过它带了版本控制功能，而且更加高效。Git里有些命令可能不是很好理解（如解决合并冲突用git add），但是对于系统层而言，它是最高效的，就像是C语言的数组下标从0开始一样。
