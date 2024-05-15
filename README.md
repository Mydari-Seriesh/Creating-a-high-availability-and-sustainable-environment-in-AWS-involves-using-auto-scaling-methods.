![image](https://github.com/Mydari-Seriesh/Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods./assets/169886237/8bfcebb0-7365-46fa-bf3e-9e807b8089a6)# Creating-a-high-availability-and-sustainable-environment-in-AWS-involves-using-auto-scaling-methods.

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

After clicking on create subnet aa new page will be opened in that select the VPC id which you created 

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

