---
published: false
categories: hackathon
tags: >-
  skyhack aic chhattisgarh incubator hackathon android react react-native SKY
  CHIPS
---
# SkyHack 2018: Building for Disaster Relief

This blog post details my experience in participating in [SkyHack 2018](skyhack.36inc.in), a hackathon by the Chhattisgarh Government to build applications for Android Phones going to be distributed as part of the [Sanchar Kranti Yojana](https://navbharattimes.indiatimes.com/business/business-news/micromax-jio-bag-rs-1500-cr-order-from-chhattisgarh-government/articleshow/65830455.cms).

The process of participation included selecting a social problem to solve from a set of 6 statements, submitted a proposal of our solution before 31st July 2018, Implementing a PoC of the solution and pitch our solutions at 36inc, Raipur.

I participated in a team of 4, with, [Vinayakk Garg](https://github.com/vinayakkgarg), [Hardik Khurana](https://github.com/hardik0330) and [Rishab Bansal](https://github.com/rishab-rb).

# A Problem to Conquer

Out of 6 problem statements, dealing with different problems, We were intrigued by with an idea for the 3rd one

_During an incidence of natural disaster, information and time are two of the most crucial resources. So, can we source information from citizens and simultaneously disseminate it among them in an effective and targeted manner, to minimise damage and save lives?_

The problem was divided into two parts, in the first part we had to build a disaster education platform for educating people before a disaster strikes and a system to provide relief to people under duress.

Another major requirement of the `Problem Statement` was to crowdsource information and let it be easily accessible.

Along with building the ideas conceptually we made sure we had the neccessary technical skills and neccessary technical information to build our ideas. Knowledge of JavaScript was the biggest enabler, allowing us to quickly spurn up an Android Application in a matter of days.

## Our Solution

We approached the divided problem with the disaster education platform coming in first.

## Disaster Education

We took a gamified approach towards building the disaster education platform, the ideology was to build `narratives` out of preventive measures to be taken during a disasters, to take the users on a ride with paths they could choose for themselves. A choose your adventure for teaching people about disasters. `It's an Earthquake! What will you do?! Hide under the tabel or Sit on the Sofa?` (well, the PoC didn't quite end up as our imaginations)

For the second part, We were to essentially build a system to provide relief when a calamity hits or when a person was under duress. Right from the beginning of the idea, we decided we needed to keep tech on the person's phone to a minimum because getting internet connectivity during a disaster will always end up as a problem, so we relied on an assumption that 2G GSM networks were available and SMSes could be sent. Thinking a bit more practically, assuming even 2G GSM networks was a long shot during a disaster, but some kind of networking is needed to provide relief, that is why we ended up using 2G GSM as our constraint.   
