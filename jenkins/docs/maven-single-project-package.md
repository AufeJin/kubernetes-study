#### 一、创建任务
![image](https://github.com/firechiang/kubernetes-study/blob/master/jenkins/image/build01.PNG)
![image](https://github.com/firechiang/kubernetes-study/blob/master/jenkins/image/build02.PNG)
#### 二、编写脚本（注意：该机器需手动安装Maven工具）
```bash
node {
   // 定义环境变量（在其它的地方可以使用$MODULE_NAME获取该值）
   env.MODULE_NAME = "springboot-demo"
   // 拉取代码
   stage('Preparation') { // staged的名字可以随便取
      git 'https://github.com/firechiang/springboot-demo.git'
   }
   // 使用Maven打包 
   stage('Maven Build') {
      // sh 就是要执行的命令
      // 多模块工程，只打包一个模块可使用命令（mvn -pl 模块名称 -am clean package）打包
      sh 'mvn clean package'
   }
}
```
![image](https://github.com/firechiang/kubernetes-study/blob/master/jenkins/image/build03.PNG)