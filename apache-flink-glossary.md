# Apache Flink Glossary

## DAG (Directed Acyclic Graph)
A DAG in Apache Flink stands for Directed Acyclic Graph.  It is a fundamental concept used to represent the series of transformations applied to the data in a Flink program.  Each node in the DAG represents a computational operation or transformation, while the directed edges indicate the data flow between these operations.  The graph is acyclic, meaning it does not contain any cycles, ensuring that there is a clear, non-repetitive flow of data from the source to the sink.

### Components of a DAG
1. **Vertices (Nodes)**:  Each vertex represents a data transformation or a computational operation.  This could be a map, filter, join, window operation, etc.

2. **Edges**:  The directed edges indicate the data flow dependencies between the vertices.  An edge from vertex A to vertex B means that the output of operation A is used as input for operation B.

3. **Sources**:  Nodes with no incoming edges.  These represent the starting points of the data flow, usually corresponding to data sources like Kafka topics, files, or databases.

4. **Sinks**:  Nodes with no outgoing edges. These represent the end points of the data flow, where the final results are written to external systems like databases, files, or message queues.

Apache Flink, a stream processing framework, offers different deployment modes to run applications: Session Mode and Application Mode. Each mode has distinct characteristics suited to different use cases and resource management strategies.

## Flink Application Mode

**Definition:** In Application Mode, a dedicated Flink cluster is started for each job submission. The cluster lifecycle is tied to the job lifecycle.

**Characteristics:**
1. **Dedicated Resources:** Each job runs in its own dedicated cluster, ensuring no resource contention between jobs.

2. **Isolation:** Full isolation between jobs, as each job has its own cluster.

3. **Deployment:** The cluster starts when the job is submitted and stops when the job completes.

4. **Startup Time:** Potentially slower job startup due to the time taken to start a new cluster.

5. **State Handling:** State is managed within the dedicated cluster for the job.

6. **Use Case:** Suitable for environments where job isolation and dedicated resource allocation are critical.

**Pros:**
- Full isolation between jobs.
- No resource contention.

**Cons:**
- Potentially higher resource usage.
- Increased overhead for cluster startup and management.

## Flink Session Mode

**Definition:** In Session Mode, a long-running Flink cluster is started independently of the job submissions. Multiple jobs can be submitted to this cluster, which they share.

**Characteristics:**
1. **Resource Sharing:** Multiple jobs share the same cluster resources, which can lead to resource contention but allows for better utilization of resources.

2. **Isolation:** Since multiple jobs run on the same cluster, issues in one job can potentially affect others.

3. **Deployment:** Jobs are submitted to the cluster after the cluster is started.

4. **Startup Time:** Faster job startup since the cluster is already running.

5. **State Handling:** State is managed across multiple jobs in the same cluster.

6. **Use Case:** Suitable for environments where resource sharing and reduced overhead for cluster startup are important.

**Pros:**
- Efficient resource utilization.
- Reduced overhead in managing multiple jobs.

**Cons:**
- Potential resource contention.
- Lower isolation, leading to possible cross-job impact.

## JobGraph
The JobGraph represents a Flink dataflow program, at the low level that the [JobManager](#jobmanager) accepts.  All programs from higher level APIs are transformed into JobGraphs.  The JobGraph is a graph of vertices and intermediate results that are connected together to form a [DAG](#dag-directed-acyclic-graph).

## JobManager
The JobManager is an orchestrator. It is responsible for coordinating and managing different activities within a Flink application.  This includes scheduling tasks, coordinating checkpoints, and handling the execution of code (directed graphs called [JobGraphs](#jobgraph)).

## TaskManager
The TaskManager is responsible for executing the tasks assigned by the [JobManager](#jobmanager).  It has a set of slots (the smallest unit of resource scheduling) that allows it to execute multiple tasks in separate threads.