# Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods.

Administrating VPC and EC2 services by launching linux servers under Elastic load balancing rules under defined subnetworks with autoscaling method


Perquisites:
1.	Create VPC
2.	Creation of 2 Public subnets (Different availability zones)
3.	Launch 2 AWS Linux instances (Different availability zones)
4.	Create Target groups
5.	Create Load balancer
6.	Create launch configuration
7.	Create Autoscaling group.

Ans:


Step: Login to AWS management console and Go to VPC service and Create a VPC.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/c8b7359b-3545-49cd-bf00-3bc5a65ce7ba)

After Selecting the VPC option. Now select create VPC

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/915f321c-0711-438e-9a67-b82697c4b40f)

After selecting the create VPC

I had selected the below options to configure my VPC which you can see in the below image.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/1de38ead-7976-4104-b806-a8108c5bdf6d)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/973cca70-a359-4a07-b962-97a92630da9b)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/b18ecc98-54c1-4a2e-83b4-d5b6465c53fc)

As per my requirement I had created a VPC with the options of ipv4 CIDR with the subnets of 256.

After creating the VPC with 256 subnets.
Now I am going to create 2 subnets with different availability zones.
For that you need to select the option of subnets.


Step 2: Click on subnets a new will be opened in that now you need to click on create a subnet.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/fa1ab86a-06ef-4c05-beef-40c449867133)

After clicking on create subnet a new page will be opened in that select the VPC id which you created 

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/2363f58e-c6ad-4bcd-bad7-216d80e99c9e)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/ad868e83-4c6b-4a22-95da-83a9aa25e213)


In the subnet settings, enter or provide a subnet name and choose availability zones. The IPv4 VPC CIDR block is set to default. For the IPv4 VPC subnet CIDR block, we need to divide the actual subnet into two different subnets, each with 128 subnets.


![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/e9c471f9-e2c7-48e3-b412-db78d8424efc)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/f318906f-b555-473a-9ddd-08b1078fd1ae)


After that click on create subnet.
Now repeat the same process again to create a second subnet.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/30a26e64-06ca-47fd-8ee2-4329c6a13d68)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/26070042-ce30-4d86-9343-8156fed9258c)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/7dc0c6ad-acfd-4d84-b2ce-44e6b8f8995f)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/5b10bb50-5fb2-444c-aa99-d7b54be1b464)

As you can see, I have created two subnets with different availability zone.

Now we need to provide the internet connection to the VPC and both subnets.

To do that we need to select the internet gateways

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/23c87fa5-df65-4e50-b04d-412fb4345187)

After selecting the internet gateways now we need to select or click on create internet gateway

After click on it a new page will be opened and in that you need to enter the name  and click on create.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/fe87e33f-c9ec-4f30-9caa-2c97e97bdab6)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/8cc002be-677a-4075-a500-948cc714c8a9)


As you can see the above pic I have created the internet gateway. Now I need to attach the internet gateway to the VPC which had created earlier.

To do that select the internet gateway which you have created just now and go to action, attach VPC

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/e218dec0-e934-4861-974b-39a12533567c)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/1a1f84d0-7236-4356-8d8d-e7a5d87dd980)

As you can see the above pic I have created the internet gateway. Now I need to attach the internet gateway to the VPC which had created earlier.

To do that select the internet gateway which you have created just now and go to action, attach VPC

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/92fe98c8-d15b-41c9-aafd-76d75f832626)


![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/6fc554c1-95a1-44ad-b62b-2758e99287b5)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/bd54179c-1936-45e7-8aa2-4e55ac385c42)

As you can see, I have attached the internet gateway to the current VPC but still we didn’t provided internet to access to the subnets.
To do that now we need to create a route table and add both the subnets to it and change the route.
To do that first we need to create route tables. Now click on route tables and select create route tables a new page will be opened in that enter the name and select the VPC next create route tables.


![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/ca704c9a-3006-49cc-9aa3-3f5a9699fc1d)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/04badfa6-a503-4cac-9156-7bdd65861ab6)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/77330554-c579-4bbf-b3a6-135b0f2a492d)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/3be5c876-37c6-4fd3-98ea-e98200b1740e)

As you can see, I have attached the internet gateway to the current VPC but still we didn’t provided internet to access to the subnets.
To do that now we need to create a route table and add both the subnets to it and change the route.
To do that first we need to create route tables. Now click on route tables and select create route tables a new page will be opened in that enter the name and select the VPC next create route tables. 

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/228f15b9-5596-4f8f-88d7-c10dec92658d)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/392122f8-dd59-4de6-bf4a-c5e2dcfb8934)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/8b898372-918a-40d8-bbc4-faa216991bfb)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/8def87ad-d13d-49c7-be6a-5c67a98beec7)

As you can see, I had created route tables.

Now Go to subnets associations and add two subnets which we have created earlier.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/46412a17-c191-4851-b26e-52ff02eff02c)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/eb147602-d693-43e3-bb56-51b3766c0d80)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/76a8bb12-6972-40da-a62d-87528205b944)

As you can see, I have added both the subnets into the subnet associations.

Now go to routes and select the edit the routes and click on add route,
In add route select the destination as anywhere and Target as internet gateways and select the internet gateway which you have created earlier
And save changes

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/0701d96d-1cc1-4c7a-a7bd-09497e037075)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/584944c5-85fd-4c35-9574-c9208c3e2725)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/d26a4b84-64a6-40b4-b532-bec0d6d8134c)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/d257b654-ff1d-40d8-ab00-20316196aff8)

As you can see, I have provided internet connection to the both subnets.

Step 3: Now we need to create two ec2 instance with Linux AMI
	Go to AWS management console.
	Search for EC2.
	Click on E2 service and new page will be opened.
	In that page select instances and click on Launch instance.
	Enter or give a name for your instance.
	Add Linux AMI.
	Select instance type t2 micro storage.
	Add your VPC which you have created earlier add a subnet also.
	Add security group.
	Add or create key pair.
	Click on create or launch instance.
	In advance you can add a script also.
	Your instance will be created.
	After you done with one ec2 instance you can create another one with same setting and repeat the same steps for other one.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/c1c91298-fd7b-477f-93da-b824387589c4)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/f6f6cebc-c9c2-45bf-b504-e3c0e748b8aa)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/abd35329-3d5b-4551-aa57-5bbb626be530)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/9676f228-28f7-42cb-897d-8f85e372e658)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/ebbe84a0-d692-403e-9bd0-f8a97ea62f46)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/fc22623e-196f-4c5a-a5bb-bebb8898a144)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/5185013c-5a8f-4319-b6e7-37bd04c1b650)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/9875127b-de3a-4a30-8241-7c9aa010803c)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/df05dfb0-b390-4125-929d-316f935eb22d)

As you can see , I have created two ec2 instance.

Step 4: Target groups
	We are creating target groups on ec2 instance. Where later it will used in load balancer.
	To create a target group.
	Go to load balancing option which you can see in ec2 service page.
	Below the load balancer option, you can see target groups.
	Select the target groups and new page will be opened.
	In that page select to create target groups
	 A new will be opened where you need specify the group details.
	Select instance.
	Enter your target group name.
	Select HTTP Port :80
	IP address type: IPv4 CIDR block
	Add the VPC which you have created earlier.
	And leave everything as it is.
	Select next.
	A new page will be opened. Where it asks to register your targets.
	Add both the instance which you created earlier.
	And select include the pending below.
	Now click on target group.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/c982ca0a-4e29-4d40-96b1-e059ee0c75f1)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/8b85116a-e3f8-4f09-b123-df6220243fe0)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/69838922-dde7-4062-a495-81019c97bc24)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/86e58efd-bf3c-46d2-b530-0fb13ce65f42)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/dd0d7e81-4c5c-45ab-9ffe-fb54d28f63a8)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/5fb74857-3a82-42dc-8c7e-a207be316aa3)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/bc45d49b-7c64-4206-9710-93443b4a21bd)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/e74694ae-20ae-4cc4-ae46-31ae1e12ccfe)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/5e853971-aba8-4308-9f96-66f724c0c784)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/74b49efb-2894-444f-8970-492fd4fc5ace)

As you can see, I have created target group for ec2 instance.

Step 5: Load balancer
	To Create Load balancer.
	Select Load balancer service.
	A page will open in that you need to select the Application load balancer because we creating for instance to work under high availability and sustainability.
	After that a new page will be opened.
	In that is ask for some basic configuration,
	Add or enter the name.
	In Scheme select internet facing.
	IP address type: IPv4
	In Network mapping add VPC which we created and used so far.
	Add availability locations 
	Add security group.
	In listeners and routing add the target group which we created earlier.
	Where it shows the option when click on target group.
	Select to create load balancer. 

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/dff860c1-cd72-4bb3-9fac-531bbe0bb4a3)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/3473efe2-624f-4a78-81d5-4c65f45cefd1)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/ee32b6e0-414c-47bb-8545-55a095968973)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/9258d65e-4908-45de-ad01-35303cdfecae)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/dd84f413-9ece-41cd-a522-cfd996711ef7)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/a4a1a090-14b5-4dc1-b058-528f1d80ba0a)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/dbd92536-977d-468d-b039-a717b26077f1)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/c0d8db34-bd3e-414e-82ff-44c8e4ed592a)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/c5cb82eb-6045-4117-a70c-0e921362abbc)

As you can see, I have created an application load balancer.

 Step 6: Before create lunch template we need take a backup of ec2 instance to determine the rule and regulation of the template.

	For go to instance and select the instance id which we need to backup and use for the template.
	Then go to action and click on image and template.
	After click on image and template it will show three options.
	Select create image.
	It will ask for some basic details.
	Enter the image name.
	Now click on create image.
	Your image will be created.
	To check go to Image and select AMI.
	You can see the snapshot of your AMI.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/8a208729-86ee-476f-8efd-d55d39b87091)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/d89138bd-bebd-4de1-bd99-728567db1e7f)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/9ba350d2-174f-4276-b0dd-febfee6aecbd)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/37dd703b-a8ca-4812-a9bd-4f36593faad4)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/d4d6266f-9efc-4d6f-90e5-367f386954d1)

As you can see, I had taken a snapshot of the Ami.

Step 7: Now we can continue the process for creating a launch template for auto scaling group.
	Go to Auto scaling group
	Select to create Auto Scaling group.
	Enter the name of auto scaling group.
	In launch template option select to create launch template.
	A new page will be opened.
	Enter the name of the template.
	In AMI option Select the template which you had taken the snapshot of the AMI. 
	In instance type add t2 micro.
	Add Key pair.
	Don’t add any subnet.
	Add security group
	Click on launch template.
	Your template will be created.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/4180d747-ed35-4759-8186-0e0b1ef09375)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/59a78f33-db93-4060-a9a2-f7c925555bd0)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/c39e9296-918a-4265-9d68-62b1fe70902e)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/9f42fa56-c25e-4fa8-b18f-18657d6da9e9)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/02503006-e8e0-4184-8e8a-d8078d9006be)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/a410d66d-e9a5-42d0-9e04-4366662beac9)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/05d8fc4c-d5c0-4bac-9548-3682423ecca8)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/272940da-020e-4531-ae00-4373148f2e4a)

As you can see, I had created launch template.




Step 8: Creating Auto Scaling group.
	To Create Auto Scaling group.
	Select Auto scaling group.
	Enter Auto scaling group name.
	Add the template which we had created earlier and click on next.
	A new page open in network add the VPC both the subnet which used earlier and click on next
	In advance option add the auto scaling group to existing load balancer.
	Add the target group which we have created and click on next.
	In Group Size for desired capacity add 2.
	For scaling min 1 and max 2 and click on next.
	Add notification if you needed.
	Add tags if you need and review your options.
	Select to create auto scaling group.

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/8cdab032-ba9a-4b0e-a0b9-59f4cc7127cc)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/b29adcfa-ebfb-4ac5-a00d-4a1e222322b6)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/c22bfbd3-94e3-46c8-a3b8-c0add14b1f92)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/637f5162-2e60-4b90-be94-e9bc308697c6)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/f1ac87b0-c1c4-4371-8f71-03ecf5e442f1)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/0b94da44-e37b-4194-8d4f-375983721d6b)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/d72d2d02-eedb-4102-b852-d7452f29ceaa)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/22536ea7-f916-4479-945c-b3965e438321)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/97ad6698-75a0-4884-be55-7795ad998723)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/59f0b0da-a793-4c88-bd58-6964c2ecc90e)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/24a499ad-9932-4345-92c5-641166485e75)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/749423df-3243-4fad-bb36-c0097342bfd3)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/51fbd99f-90b2-4dab-83b6-5212eb52e6a2)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/f694546a-8305-4ca4-8079-0145d3fcc92f)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/caed3822-b606-4f78-874b-b58f9af88a50)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/a8846458-3610-4103-bdc7-647e8f26e840)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/de89ab4d-d4b8-4e41-8c85-3247719bdd04)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/1c9d5a0b-b892-4dda-9afc-4815abb262bc)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/43134dd0-ab71-4c9f-ad53-ecfc1eae176a)
![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/7264605b-6e8f-4240-a769-cfb06b284757)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/8df3975d-6456-42f3-bd9f-9a9448425783)

As you can see, I have created the auto scaling group which attached existing load balancer.
The auto scaling group helps us in scale in and scale out depending upon the incoming traffic and if any instance is unhealthy, it will automatically remove the instance and replace with a new instance and control the incoming traffic.  

Testing load balancer:


![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/86b545a7-61d9-4657-962d-1d652c2d90a8)


![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/37b1c6e3-b073-41f0-843d-fa15be9271ce)

![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/42307e80-7d09-432d-a814-a30eeac17f87)
