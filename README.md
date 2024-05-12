# elements-of-ai-idea

Final project for the Building AI course at https://www.elementsofai.com/

## Summary

Utilise reinforcement learning to augment resource scheduling decisions in a virtualization environment by training an agent to make optimal decisions based on the current state of the system.

## Background

Consider a virtual machine for example, which is to be deployed into a virtualisation host. 
If you have _n_ hosts to choose from, which one do you choose? Naive implementations consider only
available resources, meaning does a virtual machine with a given configuration fit into a host in
terms of CPU and RAM, for example.

As an example of an improved scheduling implementation, we can refer to the Kubernetes container
scheduler ("kube-scheduler"). It operates on a 2-step process. First available nodes are filtered 
based on available resources. The second step is to score filtered nodes based on a set of scoring rules. The node with the highest score is selected. For more details, see
[scheduler chapter on Kubernetes documentation](https://kubernetes.io/docs/concepts/scheduling-eviction/kube-scheduler/).

In both cases, the quality of these scheduling decisions is often something the end-user or operator
is unable to influence. In some environments, having maximum resource utilisation even with
the cost of lower class of high-availability would be ideal. In other environments, energy efficiency
might be the main factor. Neither example also measure whether the decision was a good or a bad one,
while functionality was achieved.

Augmenting the scheduling process through reinforcement learning allows the system to factor in a lot
of information that's currently not used. It allows the system to learn how the workloads operate, for
example how much CPU is actually used vs. allocated.


Which problems does your idea solve? How common or frequent is this problem? What is your personal motivation? Why is this topic important or interesting?

This is how you make a list, if you need one:
* problem 1
* problem 2
* etc.


## How is it used?

Describe the process of using the solution. In what kind situations is the solution needed (environment, time, etc.)? Who are the users, what kinds of needs should be taken into account?

Images will make your README look nice!
Once you upload an image to your repository, you can link link to it like this (replace the URL with file path, if you've uploaded an image to Github.)
![Cat](https://upload.wikimedia.org/wikipedia/commons/5/5e/Sleeping_cat_on_her_back.jpg)

If you need to resize images, you have to use an HTML tag, like this:
<img src="https://upload.wikimedia.org/wikipedia/commons/5/5e/Sleeping_cat_on_her_back.jpg" width="300">

This is how you create code examples:
```
def main():
   countries = ['Denmark', 'Finland', 'Iceland', 'Norway', 'Sweden']
   pop = [5615000, 5439000, 324000, 5080000, 9609000]   # not actually needed in this exercise...
   fishers = [1891, 2652, 3800, 11611, 1757]

   totPop = sum(pop)
   totFish = sum(fishers)

   # write your solution here

   for i in range(len(countries)):
      print("%s %.2f%%" % (countries[i], 100.0))    # current just prints 100%

main()
```


## Data sources and AI methods
Where does your data come from? Do you collect it yourself or do you use data collected by someone else?
If you need to use links, here's an example:
[Twitter API](https://developer.twitter.com/en/docs)

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

## Challenges

What does your project _not_ solve? Which limitations and ethical considerations should be taken into account when deploying a solution like this?

## What next?

How could your project grow and become something even more? What kind of skills, what kind of assistance would you  need to move on? 


## Acknowledgments

* list here the sources of inspiration 
* do not use code, images, data etc. from others without permission
* when you have permission to use other people's materials, always mention the original creator and the open source / Creative Commons licence they've used
  <br>For example: [Sleeping Cat on Her Back by Umberto Salvagnin](https://commons.wikimedia.org/wiki/File:Sleeping_cat_on_her_back.jpg#filelinks) / [CC BY 2.0](https://creativecommons.org/licenses/by/2.0)
* etc