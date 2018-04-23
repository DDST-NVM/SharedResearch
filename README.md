## What is Shared Research?

This repository is targeted for the new project: Distributive Persistent Memory File System.

We share papers, techniques, ideas by building, modifying and reviewing files.

## Why do we Share?

We should push ourselves forward, or we can hardly *grow up*.

We should make our goals clear, or our project can never start.

We should communicate with each other, or the research ideas just get rotten.

## How to Use?

The principle is very simple: each one should read at least two papers a week (carefully for one and loosely for the other), write week report in directory `ReadingList/`.

Please prepare your own github account and you will be added to this repository group by the administrator.

### How to Use Git

Please refer to the References below.

**References**

[廖雪峰的Github教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
[Github简明教程](http://www.runoob.com/w3cnote/git-guide.html)


### Step-by-step Operation (Under Unix Terminal or Git Shell)

For example, my name is Cui Dawang and I have read two papers named A.pdf (FAST) and B.pdf (OSDI) 

``` 
git clone https://github.com/DDST-NVM/SharedResearch.git
cd SharedResearch/
cd ReadingList/
vim README.md (Read the notice for writing week report)
mkdir CuiDawang
cd CuiDawang
cp ../HuangKaixin/hkx-template.md  ./cdw.md
vim cdw.md (fill content in this file according to hints and HuangKaixin/hkx.md)
cd ../../Papers/
mkdir FAST; mkdir OSDI (if the dir exists, then you don't have to create it)
cp pathToPaperSet/A.pdf 
cp pathToPaperSet/B.pdf
cd ../
git add .
git commit -m 'write your own comments here to help others know what is updated'
git pull (it's a good habit to pull before you push)
git push origin master (for https method, you have to input your Github account and password then)
```
