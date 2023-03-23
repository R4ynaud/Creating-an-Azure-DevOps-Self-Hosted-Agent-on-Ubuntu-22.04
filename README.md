# Creating an Azure DevOps Self Hosted Agent on Ubuntu 22.04

![image](https://user-images.githubusercontent.com/93924485/227070225-c02f7135-d6e9-44b8-b058-d8c3c5f0cab5.png)



## Azure DevOps Self-Hosted Agent nedir, ne işe yarar ?

• Azure DevOps Self-Hosted Agent, Azure DevOps'ta kullanılan bir araçtır. Bu araç, Azure DevOps'ta yer alan CI/CD süreçlerinin yönetilmesinde kullanılır. 
Kendi bilgisayarınızda veya sunucunuzda çalışan bir agent olarak görev yapar ve Azure DevOps'ta yer alan görevleri yerine getirir. 
Bu sayede, Azure DevOps üzerinde bulunan projelerin, kendi altyapınızda veya sunucunuzda da sorunsuz bir şekilde çalışmasını sağlar. 
Özellikle güvenlik gerektiren veya yüksek performans gerektiren projelerde kullanılmaktadır. Bu sayede tüm serverlarınızı daha efektif bir şekilde kullanabilirsiniz.




## What is an Azure DevOps Self-Hosted Agent ?

• Azure DevOps Self-Hosted Agent is a tool used in Azure DevOps for managing CI/CD processes. It functions as an agent running on your own computer or server and performs tasks in Azure DevOps. 
This enables projects in Azure DevOps to run smoothly on your infrastructure or server. It is especially useful for projects requiring high security or high performance, allowing you to use all your servers more effectively.





### 1-) Kurulumdan önce işletim sistemimizin paketlerini güncellemek için aşağıdaki komutları çalıştırıyoruz.
###     We run the following commands to update our operating system's packages before installation.


> sudo apt-get update  
> sudo apt-get upgrade


### 2-) Eğer işletim sistemimizde "WGET" yüklü değilse öncelikle wget kurulumu yapmamız gerekiyor, wget kurulumu yapmak için aşağıdaki komutu çalıştırın.
###     If "WGET" is not installed on our operating system, we need to install it first. To install WGET, run the following command.


> sudo apt-get install wget


### 3-) Agent için yeni bir klasör oluşturuyoruz. 
###     We are creating a new folder for the agent.


> sudo mkdir azure-agent


### 4-) Organization Settings → Pipelines → Agent Pools a tıklayalım ve yeni bir pool oluşturmak için “Add Pool” a tıklayalım.
###     Let's click on Organization Settings → Pipelines → Agent Pools and to create a new pool, click on "Add Pool".


![image](https://user-images.githubusercontent.com/93924485/227314978-f0ae396c-6749-43dd-83c7-3d74b6fe5fde.png)


![image](https://user-images.githubusercontent.com/93924485/227315123-761b809f-8b40-465f-a15f-5525ce64152f.png)


![image](https://user-images.githubusercontent.com/93924485/227315305-dd2d6123-97c7-4736-8cfd-fe6829abb204.png)


![image](https://user-images.githubusercontent.com/93924485/227316597-94a6302e-b8d3-420c-875f-965fa5fab370.png)




