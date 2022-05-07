# Metaflow presentation

Created: April 24, 2022 7:32 AM

# 1. Introduction to Metaflow

### Food for thought: MLOps

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled.png)

[Why data scientists shouldn't need to know Kubernetes](https://huyenchip.com/2021/09/13/data-science-infrastructure.html)

### Metaflow Introduction

- Developed at **Netflix** and maintained by Outerbounds.
- Active contributions (or collaboration) from the community (SAP and etc.)
    - UI tool development
    - Kubernetes & Argo support

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%201.png)

### Concept

Abstraction-driven framework!

### **Infrastructure Stack for Data Science**

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%202.png)

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%203.png)

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%204.png)

### Should I Use Metaflow?[](https://docs.metaflow.org/introduction/what-is-metaflow#should-i-use-metaflow)

If you are working on an existing data science project, or you are planning to start a new one, consider the following questions:

1. **Scalability**: Do you need more than one laptop-size computer in the project?
2. **Criticality**: Is it important that results are produced correctly and in a timely manner?
3. **Complexity**: Does the project have many moving pieces or many people working together?

### **The Philosophy of Metaflow**

- Metaflow was originally designed and built to address **practical pain points of data scientist at Netflix**.
- Don't expect the current version of Metaflow to be a perfect manifestation of these principles. **Metaflow is being actively developed**. **However, much of the foundation exists, and it has proven to be successful at Netflix.**
    
    ### **Grounded on common, real-life business-oriented ML use cases**
    
    - We don’t focus on exotic, large-scale, specific use cases like real-time bidding or self-driving cars. Instead, we focus on the widest variety of ML use cases, many of which are small or medium-sized, which many companies face on a day to day basis.
    - We don’t expect the users of Metaflow to be unicorns who are experts in software engineering and machine learning. Nor we expect our users to care about ML infrastructure. Metaflow helps them to get their job done.
    
    ### **Manage entropy with code**
    
    - The first tenet implies that we must manage a great amount of inherent, irreducible complexity. Many ML infrastructures rely on GUIs, configuration, DSLs, or automation - we don’t. Most of these modalities fail to scale in terms of increasing complexity.
        
        We rely on code. General-purpose programming languages are arguably the most effective tool in building functional systems for complex use cases. The main downside of code is a steeper learning curve: for the simplest use cases, almost any other modality would provide a simpler solution. To minimize this cost, we rely on easy to learn, popular languages like Python or R.
        
    - **Fanatic focus on the usability and ergonomics**
    - **Enable collaboration**
    - **First-class support for both prototyping and production**
    - **Straightforward scalability**
    - **Pragmatic approach to data access and processing**
    - **Failures are a feature**

# 2. Metaflow overview

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%205.png)

- **A flow is the smallest unit of computation that can be scheduled for execution**. Typically, a flow defines a workflow that pulls data from an external source as input, processes it in several steps, and produces output data.
- Metaflow infers a directed (typically acyclic) graph based on the transitions between step functions.
- **A step is the smallest resumable unit of computation**. It is implemented by the user as a method that is decorated with the `@step`decorator in a flow class.
- The behavior of a step can be modified with decorators.
- Step code is the body of a step. It implements the actual business logic of flow.

# 3. DAG examples

## Linear

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%206.png)

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%207.png)

## Join

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%208.png)

## Foreach

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%209.png)

## DAG examples

[metaflow/playlist.py at master · Netflix/metaflow](https://github.com/Netflix/metaflow/blob/master/metaflow/tutorials/03-playlist-redux/playlist.py)

# 4. More features

- Features (Development)
    - Decorator-based resource management
    - Failure-first
    - Visualization
    - Managing dependencies
    - Collaborations
        
        [Basics of Metaflow | Metaflow Docs](https://docs.metaflow.org/metaflow/basics)
        
- Features (Production)
    - with Argo (K8S) or Batch / Step (AWS)
        
        [Scheduling Metaflow Flows with Argo Workflows | Metaflow Docs](https://docs.metaflow.org/going-to-production-with-metaflow/scheduling-metaflow-flows/scheduling-with-argo-workflows)
        

# 5. Internals of Metaflow

![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%2010.png)

- Provide a highly usable API for structuring the code as a workflow, i.e. as a directed graph of steps (**usability**).
- Persist an immutable snapshot of data, code, and external dependencies required to execute each step (**reproducibility**).
- Facilitate execution of the steps in various environments, from development to production (**scalability**, **production-readiness**) → No need to create Dockerfile or YAML..
- Record metadata about previous executions and make them easily accessible (**usability**, **reproducibility**).

# 6. Updates

- Infra abstraction (Metaflow) + Orchestration (AWS or Kurbernetes)
    
    [Human-Centric Data Science on Kubernetes with Metaflow](https://outerbounds.com/blog/human-centric-data-science-on-kubernetes-with-metaflow/)
    
    [Data Scientists Don't Need to Know Kubernetes with Metaflow - Outerbounds](https://outerbounds.com/blog/kubernetes-to-metaflow/)
    
- Metaflow UI & Model cards
    
    [Notebooks In Production With Metaflow - Outerbounds](https://outerbounds.com/blog/notebooks-in-production-with-metaflow/)
    
    ![Untitled](Metaflow%20presentation%20aab6883b9b024cb580229e27fb35766b/Untitled%2011.png)
    

# 7. Further readings

[All about Metaflow, a single coherent framework for data science](https://www.youtube.com/watch?v=OH0Y_DUZu4Y&t=864s)

[Effective Data Science Infrastructure](https://www.manning.com/books/effective-data-science-infrastructure)
