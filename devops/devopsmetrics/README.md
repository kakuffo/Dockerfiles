# DevOps Matrics

* Lead time to develop an application: Helps you understand how quickly you develop applications
* Percentage of failed deployments: Tells you whether they deploy successfully
* Customer ticket volume: Indicates how many issues crop up
* Mean time to recovery: Shows how long it takes to recover from an application bug or failure
* User volume: Indicates how useful your users find your applications

## Lead time to develop
“Lead time” is a term borrowed from the manufacturing method known as Lean or Toyota Production System, where it is 
defined as the time elapsed between a customer placing an order and receiving the product ordered.  For DevOps, a methodology
that encompass the practice of continuous integration, continuous testing, and continuous deliver, I take the lead time
to development as the lead time the 'lead time to production'.  Meaning, the time it take for a development artifact 
(code + configuration) to be deployed on production from the time a unit test build for that deployment is started in 
a build server such as Jenkins.

![Lead Time to Deployment](https://github.com/kakuffo/Dockerfiles/blob/master/vid/lead-time-diagram.png)

## Percentage of failed deployments

While a failure rate of 0 is the magic number, less than 5% failed deployments is considered workable. In case the 
metric consistently shows spike of failed deployments over 10%, the existing process needs to be broken down into 
smaller segments with mini-deployments.


## Mean time to recovery
Mean time to recovery (MTTR) is the average time that a device will take to recover from any failure. Examples of 
such devices range from self-resetting fuses (where the MTTR would be very short, probably seconds), up to whole 
systems which have to be repaired or replaced.

![Mean time to recovery](https://github.com/kakuffo/Dockerfiles/blob/master/vid/mtbf.png)