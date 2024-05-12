# elements-of-ai-idea

Final project for the Building AI course at https://www.elementsofai.com/. Completed the course in May 2024.

## Summary

Utilise reinforcement learning to augment resource scheduling decisions in a virtualization environment by training an agent to make optimal decisions based on the current state and past use of the system.

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

Augmenting this process with reinforcement learning would allow the system to make more optimal decisions. It factors in a lot more information that's currently not used. As an example, create
a feedback loop how much each workload has actually used the CPU it was allocated with and when.

My main motivation to this idea comes from years of experience of building and maintaining such
environments. Workload scheduling is often looked as a forward-only process, where only the state of
the system upon making a scheduling decision matters.

## How is it used?

The system designed here will take in data from a resource scheduling request, typically consisting
of multiple features. Whenever a new resource is created or scheduled, a request is created. Environments
have a scheduler already, but the system described here could be used to augment the previous method.

The system could be used by anyone who operates a system that's scheduling resources, such as Kubernetes
or a virtualisation platform. It could be bundled with a readily available pre-trained model, but due to to the nature of the problem fine-tuning or even re-training the model would be likely required.

Steps involved for creating the system:

- Train an agent about the state of the system ("state space")
- Train an agent about possible scheduling decisions ("action space")
- Define the reward function, which provides qualitative feedback of the decisions that were made, based on available metrics (such as resource utilisation, energy consumption)
- Implement the reinforcement learning algorithm
- Train the agent by running simulations or experiments
- Evaluate and fine-tune the algorithm and parameters if necessary

## Data sources and AI methods

Reinforcement learning for resource allocation has been researched in at least these
research papers:

- "Reinforcement Learning for Autonomic Resource Allocation in Clouds: Towards a Unified Approach" by Faraz Fatemi Moghaddam, Mohammad Mahdi Rezaei Youzhi, and Alberto Leon-Garcia
- "Deep Reinforcement Learning for Multi-resource Multi-machine Job Scheduling" by Zhiyuan Xu and Yuxiong He
- "Resource Management with Deep Reinforcement Learning" by Hongzi Mao, Mohammad Alizadeh, Ishai Menache, and Srikanth Kandula

A local virtualisation environment, a lab environment or a cloud environment would be sufficient as a
data source for gathering training data, but also for simulations.


## Challenges

Safety, reliability and stability are super important for a decision-maker process that sits at the
critical path of scheduling resources.

State space for any virtualisation environment is often large and complex to capture. Capturing all
meaningful parameters might lead to a complex high-dimensional state space. Same applies to the
action space.

Learning through rewards or penalties as dictated by the reward function takes time. The impact of the
decision might not be immediately apparent. These delays might be difficult to capture through the reward
function.

Scoping the project initially to specific type of workloads might be an approach worth taking. Treating
the reinforcement learning process as an augmentation rather than sole decision maker, scoping it to
specific problems and building the knowledge that way would likely work. The opinionated way.

## What next?

Building it the opinionated way as described above and gathering user feedback would be next.
While the environments can be simulated, real world scenarios and feedback is an absolute must for the
project to succeed. This would require input from people who operate various large workloads across
different environments.

## Acknowledgments

I wrote an OS task scheduler once and I always wondered how I could make the feedback loop work.
I would like to thank the "Building AI" course & staff for the great course, and for sparking my interest in ML again, after a hiatus.
