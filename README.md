# Creating an Azure DevOps Self Hosted Agent on Ubuntu 22.04

![image](https://user-images.githubusercontent.com/93924485/227070225-c02f7135-d6e9-44b8-b058-d8c3c5f0cab5.png)



## Azure DevOps Self-Hosted Agent nedir, ne işe yarar ?

• Azure DevOps Self-Hosted Agent, Azure DevOps da kullanılan bir araçtır. Bu araç, Azure DevOps da yer alan CI/CD süreçlerinin yönetilmesinde kullanılır. 
Kendi bilgisayarınızda veya sunucunuzda çalışan bir agent olarak görev yapar ve Azure DevOps da yer alan görevleri yerine getirir. 
Bu sayede Azure DevOps üzerinde bulunan projelerin, kendi altyapınızda veya sunucunuzda da sorunsuz bir şekilde çalışmasını sağlar. 
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


![image](https://user-images.githubusercontent.com/93924485/227317323-06771e57-7f7a-4494-b3ff-b8580c1915f3.png)


### 5-) Açılan ekranda pool için isim ve açıklama yazmanız gerekmektedir. Tüm pipelinelara erişim yetkisi vermek için “Grant access permission to all pipelines” ı seçebilirsiniz.
###     On the screen that appears, you need to enter a name and description for the pool. You can select "Grant access permission to all pipelines" to give access permission to all pipelines.


![image](https://user-images.githubusercontent.com/93924485/227319502-03cdf517-4a14-4d6f-9938-54a1535e9149.png)


![image](https://user-images.githubusercontent.com/93924485/227319940-75e5a738-3dd8-4a09-a417-b6f1523f6124.png)


• Yukarıdaki adımları tamamladıktan sonra bizi aşağıdaki ekran karşılamaktadır.

• After completing the above steps, we are greeted with the following screen.


![image](https://user-images.githubusercontent.com/93924485/227321665-dae0a4a2-fdae-4af8-bf8d-14d24af72d6c.png)


### 6-) “New agent” a tıklayalım. İşletim sistemine göre agentı indirmeniz gerekmektedir.
###     Click on "New Agent". You will need to download the agent according to your operating system.


![image](https://user-images.githubusercontent.com/93924485/227365596-5678c1cc-6202-4c36-b1bb-ee3f4817bb72.png)


### 7-) Agent'ı indirmek için aşağıdaki komutu çalıştırıyoruz.
###     We use the following command to download the agent. 


> wget https://vstsagentpackage.azureedge.net/agent/2.218.1/vsts-agent-linux-x64-2.218.1.tar.gz


![image](https://user-images.githubusercontent.com/93924485/227368789-fe2b82d0-c1f5-4139-8500-4c4a088dc840.png)


### 8-) ".tar" uzantılı arşiv dosyasını bulunduğumuz klasöre çıkartmak için aşağıdaki komutu çalıştırıyoruz. 
###     We run the following command to extract the ".tar" archive file to the current directory.


> tar -xvf vsts-agent-linux-x64-2.218.1.tar.gz


![image](https://user-images.githubusercontent.com/93924485/227375835-965f1bbc-2127-488e-9c88-c6b0da32df92.png)


### 9-) Personal Access Token’ı oluşturalım, bunun için aşağıdaki adımları sırasıyla uygulamamız gerekiyor. 
###      Let's create a 'Personal Access Token' by following the steps below in order.


• User settings → Personal Access Token → New Token 


• Burada hangi organization için bu agenta yetki vermek istiyorsanız onu seçmelisiniz. 
Sonrasında expiration için 30–60–90 günlük yerine “Custom defined” seçeneği ile daha uzun bir süre verebilirsiniz, 1 seneyi aşmamak koşuluyla. 


• Here, you should select the organization for which you want to authorize this agent. Afterwards, 
you can provide a longer expiration period by selecting the "Custom defined" option instead of 30-60-90 days, provided that it does not exceed 1 year.


![image](https://user-images.githubusercontent.com/93924485/227384444-e96beff2-a1fb-4b34-9769-413afee9e70d.png)


![image](https://user-images.githubusercontent.com/93924485/227384811-79aa6ff8-6d7f-485d-a278-d10c4cc9fe51.png)


![image](https://user-images.githubusercontent.com/93924485/227384874-64e1b750-4662-4584-ba77-04f2cba1e0ff.png)


![image](https://user-images.githubusercontent.com/93924485/227385155-fea9d616-44f8-4511-8993-60782934ee7a.png)


### 10-) Personal Access Token’ı oluşturduktan sonra aşağıdaki gibi bir mail almamız gerekiyor.
###      After creating the Personal Access Token, we need to receive an email like the following.


![image](https://user-images.githubusercontent.com/93924485/227385873-2989ddc6-6576-47cd-b331-37490a27b60b.png)


### 11-) " config.sh " çalıştırıp agentı create etmeye başlıyoruz, bunun için aşağıdaki bazı komutları sırasıyla çalıştırmamız lazım.
###     We need to run some commands in order to create the agent by running "config.sh". Here are the commands that we need to run in order.


> export AGENT_ALLOW_RUNASROOT="1"

> ./config.sh

> Y

> https://dev.azure.com/Organization Name

> PAT

> Agent Pool Name (Dogukan)


### 12-) Agent'ı sorunsuz oluşturduktan sonra aşağıdaki gibi bir çıktı almamız gerekiyor.
###      Once the Agent is created successfully, we should receive an output like the following.


![image](https://user-images.githubusercontent.com/93924485/227389078-97337939-1581-48d5-bfde-3468c818ca55.png)


![image](https://user-images.githubusercontent.com/93924485/227389286-e07db64d-6f11-48f3-9129-280a9d97c8ac.png)


### 13-) " Offline " olan agentı çalıştırmak için " run.sh " çalıştırmamız gerekiyor. 
###      To run the agent that is "Offline", we need to execute "run.sh".


> ./run.sh


![image](https://user-images.githubusercontent.com/93924485/227389984-d498153e-e25c-461e-9007-aedf633c3e83.png)


![image](https://user-images.githubusercontent.com/93924485/227390049-e32917d2-1711-486b-a308-ca42377808c2.png)


### 14-) Agentı sorunsuz oluşturduktan örnek bir projede çalıştığını test edelim.
###      Let's test if the agent works properly in a sample project after creating it.


![image](https://user-images.githubusercontent.com/93924485/227390957-e13910d7-e21f-4334-b3c5-863a4d4b6d6b.png)


![image](https://user-images.githubusercontent.com/93924485/227390744-56473bcb-d5c6-4a9b-a3a1-cf18a5afcf2f.png)


![image](https://user-images.githubusercontent.com/93924485/227394115-62160dd0-abf5-4b84-ba46-6d81f53382a7.png)


![image](https://user-images.githubusercontent.com/93924485/227394021-97aa3a84-08dd-4163-952a-b7e0e9107d36.png)


### 15-) Agent sorunsuz çalıştıktan sonra aşağıdaki gibi bir mail gelmesi gerekiyor.
###      After the successful execution of the agent, you should receive an email similar to the following.


![image](https://user-images.githubusercontent.com/93924485/227394489-6dc4e84f-b055-4cf9-b3a4-91ceac49ba7f.png)


### 16-) Agent schedule. 


#### • Profesyonel iş hayatında büyük projelerde çalışmaya başladığımız zaman bütün agentlar'ı manuel yönetmek biraz karmaşık ve zor olabilir, böyle durumlarda imdadımıza Azure DevOps'un " Agent Schedule " özelliği yetişiyor. Bu özellik, oluşturulan agent'ı tercihlerimize göre yönetmemizi sağlar. Yani agent'ı önceden planlayarak istediğimiz gün ve saat aralığında çalıştırabiliyoruz.


#### • When starting to work on large projects in a professional business environment, manually managing all agents can be a bit complicated and difficult. In such situations, Azure DevOps' "Agent Schedule" feature comes to our aid. This feature allows us to manage the created agent according to our preferences. That is, we can run the agent on the day and time range we want by planning it in advance.


• Örnek bir projede bu özelleği denemek için aşağıdaki adımları tek tek uygulamamız gerekiyor.
 

• To try this feature on a sample project, we need to follow the steps below one by one.


> Pipelines → Edit Pipelines → Triggers → Scheduled → Add 


•   ![image](https://user-images.githubusercontent.com/93924485/227399132-4df3ea67-2c34-4c91-a191-434d5b4e5d1a.png)


• ![image](https://user-images.githubusercontent.com/93924485/227399167-73ee5ea6-b6be-4cd7-a944-79dbe9e8ce44.png)


• ![image](https://user-images.githubusercontent.com/93924485/227399213-58c24703-8a9f-4fb4-89b3-8d92772403ea.png)


• ![image](https://user-images.githubusercontent.com/93924485/227399256-c7928064-5f81-4d13-9c80-6ec7b7c26490.png)


• ![image](https://user-images.githubusercontent.com/93924485/227399378-30ce3885-0294-4985-8583-cc6b360700ea.png)


• ![image](https://user-images.githubusercontent.com/93924485/227399671-0c16bc95-5c75-40f1-850e-bf274534ad2a.png)


• ![image](https://user-images.githubusercontent.com/93924485/227399744-9eb8ec29-14d5-46bf-ba78-3bb19ed5eb8d.png)


• Sorunsuz çalışıp çalışmadığını kontrol ederken dikkat etmemiz gereken alan 'Scheduled' yazan 'Summary' bölümüdür.


• When checking for smooth operation, the area we should pay attention to is the "Summary" section indicating "Scheduled".


![image](https://user-images.githubusercontent.com/93924485/227400397-a6c2586a-805b-4992-8060-9856c2329474.png)


![image](https://user-images.githubusercontent.com/93924485/227402935-755aa6a5-bdca-4f9a-9901-ab23dafde21a.png)


















































