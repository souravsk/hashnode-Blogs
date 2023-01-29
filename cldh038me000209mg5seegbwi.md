# Safeguarding Your Digital World: A Comprehensive Approach to Cybersecurity

In My Last blog, we talk about DevSecOps for *development, security,* and *operations* to automate the integration of security at every phase of the software development lifecycle(SDLC), from initial design through integration, testing, deployment, and software delivery.

In this blog, we will look into attacks, What are attacks, the Motivations of attacks, and what organizations do to prevent these attacks.

# Characteristics of an Attacker

First and foremost, all businesses and software is an attack vector to an attacker, there is no safe place we can only make places safer and less attractive for people to attack.

With that in mind, attackers are a constant threat!

Attackers will identify gaps in security by running attacks in a specific order to gain access, pull data and be successful in their mission.

Attackers can be lucky, but they will absolutely work on targeted attacks.

Compromises can be slow and persistent or fast to get to a breach. Not all attacks are going to be the same.

## Motivations of an Attacker

As a DevOps team, you are going to be provisioning infrastructure, and software and protecting these environments likely spanning multiple clouds, virtualization, and containerization on platforms.

We must consider the following:

* **How** would they attack us?
    
* **Why** would they attack us?
    
* **What** do we have that is valuable to an attacker?
    

The motivations of an attacker will also be different depending on the attacker. I mean it could just be for fun... We have probably all been there, in school and just gone a little too deep into the network looking for more information. Who has a story to tell?

But as we have seen in the media attacks are more aligned to monetary, fraud or even political attacks on businesses and organizations.

In the Kubernetes space, we have even seen attackers leveraging and using the computing power of an environment to mine cryptocurrency.

At the heart of this attack is likely going to be **DATA**

A company’s data is likely going to be extremely valuable to the company but also potentially out in the wild. It is why we put so much emphasis on protecting this data, ensuring that the data is secure and encrypted.

## Attack Maps

We now have a motive and some of the characteristics of an attacker or a group of attackers, if this is a planned attack then you are going to need a plan, you are going to need to identify what services and data you are targeting.

An attack map is a visual representation of an attack on a computer network. It shows the various stages of the attack, the tools and techniques used by the attacker, and the points of entry and exits into the network. Attack maps can be used to analyze the details of past attacks, identify vulnerabilities in a network, and plan defences against future attacks. They can also be used to communicate information about an attack to non-technical stakeholders, such as executives or legal teams.

You can see from the above description that an Attack Map should be created on both sides or both teams (teams wise this is something I am going to cover in a later post)

If you were to create an Attack Map of your home network or your business some of the things, you would want to capture would be:

* Capture a graphical representation of your app including all communication flows and technologies being used.
    
* A list of potential vulnerabilities and areas of attack.
    
* Consider confidentiality, integrity and availability for each connection/interaction within the app.
    
* Map the attacks/vulnerabilities
    

An attack map might look something like this with a key explaining what each number represents.

From this map, we might consider there to be a denial of service or some malicious insider attack and access to the S3 bucket to prevent the application from saving data or causing it to save bad data.

This map then is never final, in the same way, that your application continuously moves forward through feedback, this attack map also needs to be tested against, which provides feedback which in turn means the security posture is strengthened against these attacks. You could call this "Continuous Response" in the Security Feedback loop.

At a bare minimum, we should be following a good, better, best model to better the security posture.

* **Good** - Identify security design constraints and controls that need to be built into the software to reduce an attack.
    
* **Better** - Prioritise and build security for issues found later in the software cycle.
    
* **Best** - Build automation into script deployment to detect issues, unit testing, security testing, black box testing
    

# What do Organizations do?

So Organizations have to create **Red** and **Blue** teams to work as attackers and defenders in the security space to improve an organization's security.

Both teams work toward improving an organization's security posture differently.

The **Red** team has the role of the attacker by trying to find vulnerabilities in code or infrastructure and attempting to break through cybersecurity defenses.

The **Blue** team defends against those attacks and responds to incidents when they occur

## What is Red Team?

The National Institute of Standards and Technology (NIST) defines a **red team**  as “a group of people authorized and organized to emulate a potential adversary’s attack or exploitation capabilities against an enterprise’s security posture.” The red team plays the part of the attacker or competitor with the intention of identifying vulnerabilities in a system.

## **What is a blue team?**

NIST defines a **blue team** as “the group responsible for defending an enterprise’s use of information systems by maintaining its security posture against a group of mock attackers.” If the red team is playing offence, the blue team is playing defense to protect an organization’s critical assets.

## **Benefits of a red team vs. blue team approach**

One way organizations can assess their security capabilities is to stage a red team/blue team exercise. These two teams of professionals face off to put a security infrastructure to the test in a simulation meant to mimic a real attack. Taking a red team versus blue team approach to cybersecurity can have several benefits, allowing security teams to:

* Find vulnerabilities
    
* Strengthen network security
    
* Build experience in detecting and containing attacks
    
* Develop response plans and procedures
    
* Create healthy competition and cooperation
    
* Raise security awareness among other staff
    

So this is how organizations try to prevent or predicted the attacks that can happen to the organization.

This is one more team called Open Source Security. Let's know about it.

# Open Source Security

Open-source software has become widely used over the past few years due to its collaborative and community/public nature.

The term Open Source refers to software in the public domain that people can freely use, modify, and share.

The main reason for this surge of adoption and interest in Open Source is the speed of augmenting proprietary code developed in-house and this in turn can accelerate time to market. Meaning that leveraging OSS can speed up application development and help get your commercial product to market faster.

## What is Open-Source Security?

Open-source security refers to the practice of ensuring the safety and security of computer systems and networks that use open-source software. As we said above Open-source software is software that is freely available to use, modify, and distribute, and it is typically developed by a community of volunteers however there is a huge uptake from big software vendors that also contribute back to open-source, you only need to look at the Kubernetes repository to see which vendors are heavily invested there.

Because open-source software is freely available, it can be widely used and studied, which can help to improve its security. However, it is important to ensure that open-source software is used responsibly and that any vulnerabilities are addressed in a timely manner to maintain its security.

# THE END

Thank You for reading this blog and have a nice day.

Currently seeking #cloud #devops job opportunities. Hands-on experience in #microservices, #containerization, & #loadbalancing. Post-grad student, certified in #AzureFundamentals. Open to remote work. Let's work together to push the boundaries of technology!