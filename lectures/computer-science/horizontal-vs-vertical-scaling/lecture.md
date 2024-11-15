# Horizontal vs Vertical Scaling

## Horizontal Scaling

Horizontal scaling, also known as scaling out, involves adding more nodes to or removing nodes from a system to handle increased load. It's like adding more lanes to a highway to handle more traffic. In a distributed system, horizontal scaling can be achieved by adding more machines into the pool of resources. 

For example, in an Amazon Web Services (AWS) environment, horizontal scaling could be managed by adding more EC2 instances to your application's Elastic Load Balancer. 

```python
import boto3

# Create an EC2 resource object
ec2 = boto3.resource('ec2')

# Create instances
instances = ec2.create_instances(
    ImageId='ami-0abcdef1234567890',
    MinCount=1,
    MaxCount=5,
    InstanceType='t2.micro',
)
```

The code snippet above creates five new EC2 instances. This is an example of horizontal scaling.

## Vertical Scaling

On the other hand, vertical scaling, also known as scaling up, involves adding more power (CPU, RAM) to an existing node. In the highway analogy, it's like adding more floors to a building.

For example, in the same AWS environment, vertical scaling could be achieved by changing the instance type of your EC2 instances to a more powerful one.

```python
# Client to interact with EC2
ec2Client = boto3.client('ec2')

# Stop the instance
ec2Client.stop_instances(InstanceIds=['i-0abcdef1234567890'])

# Wait for the instance to stop
waiter = ec2Client.get_waiter('instance_stopped')
waiter.wait(InstanceIds=['i-0abcdef1234567890'])

# Change the instance type
ec2Client.modify_instance_attribute(InstanceId='i-0abcdef1234567890', Attribute='instanceType', Value='t2.large')

# Start the instance
ec2Client.start_instances(InstanceIds=['i-0abcdef1234567890'])
```

The above code stops an instance, changes its type, and then starts it again. This is an example of vertical scaling.

In conclusion, both methods have their own pros and cons. Horizontal scaling can provide a higher degree of fault tolerance, but vertical scaling can offer a higher performance per node.
