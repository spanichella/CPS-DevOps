# Testing Autonomous Cyber-physical Systems with the BeamNG Simulations Soft-Body Environment

[Introduction](https://github.com/janousy/CPS-DevOps/blob/main/README.md#introduction)<br>
[Previous Results](https://github.com/janousy/CPS-DevOps/blob/main/README.md#previous-results)<br>
[Project Goal](https://github.com/janousy/CPS-DevOps/blob/main/README.md#project-goal)<br>
[Results](https://github.com/janousy/CPS-DevOps/blob/main/README.md#results)<br>
[Future Work](https://github.com/janousy/CPS-DevOps/blob/main/README.md#future-work)<br>
[Acknowledgement](https://github.com/janousy/CPS-DevOps/blob/main/README.md#acknowledgement)<br>
[References](https://github.com/janousy/CPS-DevOps/blob/main/README.md#references)

## Introduction

Cyber-physical Systems (CPS) are systems in which physical mechanisms are typically controlled and monitored by computer-based algorithms, this by leveraging sensors-based analysis and operational data coming from the environment and domain they are operating [5]. Emerging CPS---from medical monitoring systems and devices, robotics and autonomous systems, automatic pilot avionics, and transportation---are expected to play a crucial role in the quality of life of future generations and the global economy [1].

Problem and Recent works: Current CPS development and monitoring practises have several limitations and drawbacks including:

- the difficulty to repeat and test faulty scenarios (since the environment constantly changes and it is hard to reproduce the environment in which the CPS got tested) [2];
- difficulty to ensure that CPS behaviour is safe, with incidents involving also autonomous systems [3].

A first key challenge in testing CPS in different domains is that it requires specific development and verification strategies able to include Hardware-in-the-Loop (HiL) capabilities [1]. Therefore, CPS are far more difficult and expensive to test and integrate [3], since testing the hardware is not always practically possible. The final version of the hardware is often available late and testing on the hardware directly can be expensive. A typical approach to dealing with this is to develop hardware proxies, such as system simulators and digital twins [4, 5].

## Previous Results

Our project is based on the master's thesis of [Bill Bosshard](https://github.com/billbos). Previous results can be found in his thesis [repository](https://github.com/billbos/Master-Thesis-CPS-SORTER) and within the [CPS-Sorter](https://github.com/billbos/CPS-SORTER). His complete thesis may be obtained within agreement of the Institute for Informatics at University of Zurich.

## Project Goal

In this project we investigate the usage of simulation environments and DevOps technologies to reduce the cost of testing CPS in development pipelines. Hence, we examined ways to reduce testing costs in the context of self-driving cars systems. To achieve this goal, we propose to automate the CPS-SORTER through CI-CD. The CPS-SORTER is a testing framework proposed in recent work [5], which integrates two approaches to predict the lane tracking ability for AI-based simulation engines of self-driving cars, to identify safe and unsafe roads before their executions.

### Extension Points

- Set up a DevOps pipeline based on Jenkins to conduct `self-driving quality assessment of testing scenarios, before executing them` (starting from available scenarios provided by the BeamNG) simulation environment. CI is the most important part of DevOps that is used to integrate various DevOps stages. We use Jenkins as it is a commonly used, open source automation server for Continuous Integration. It helps automating the parts of software development related to building, testing, and deploying, facilitating continuous integration and continuous delivery.

- Determine other safety critical criteria to integrate in the pipeline. To do so, other simulators are evaluated and assessed. The choice of the simulator should be based on the requirements given by the environment (e.g. the Ubuntu server provided).

## Results

### Pipeline

See [here](https://github.com/janousy/CPS-DevOps/blob/main/pipeline/README.md) for more information about the built pipeline and [here](https://github.com/janousy/CPS-DevOps/blob/main/pipeline/installation.md) for an installation guideline.

### Safety Criteria

The methodology and findings on how other safety criteria were determined can be found [here](https://github.com/janousy/CPS-DevOps/blob/main/simulator/README.md).

## Future Work

### Pipeline Extension

#### Simulator consistency

An integration of our evaluated data of the scenarios into the pipeline extension would be an ultimate goal. Therefore, the pipeline has to be adjusted to read our evaluated dataset of Carla and not only BeamNG.

#### Independent server-hosted Pipeline

Currently, the continuous integration with Jenkins requires a fixed local machine to host. To provide a seamless pipeline that is independent from any fixed local machine, Jenkins could be setup to run directly on the server. This way no local machine would be needed for a working pipeline to the server. However, with this approach the computed results would still need to be fetched manually from the server to a local machine for further analysis.

### Scenario Safety

A full explanation on future work to be done can be found [here](https://github.com/janousy/CPS-DevOps/tree/main/simulator#future-work).
Quickly summarized: The baseline for our AI agent is the pre-built one from Carla. Improving the AI agent to be more sophisticated would make the evaluation of the scenarios more meaningful. Additionally, adding configured destination points according to the scenarios would simplify the scenarios run through and evaluation. An extension of the Classification Criteria with traffic rate, weather etc. would add more sense to the evaluation alongside with building more purposeful custom scenarios for our AI to provide an extended data set.

## Acknowledgement

This project was conducted in the context of the course `Software Maintenance and Evolution`. The course is currently thaught by Dr. Sebastiano Panichella, which was also the supervisor of our project. You can find the outline of the course [here](https://www.ifi.uzh.ch/en/seal/teaching/courses/sme.html) and our final presentation of this project [here](https://github.com/janousy/CPS-DevOps/tree/main/presentation.pdf).

The following developers were involved in the project:

- Alain Küng: [alainkueng](https://github.com/alainkueng)
- Ramon Solo de Zaldivar: [solodezaldivar](https://github.com/solodezaldivar)
- Janosch Baltensberger: [janousy](https://github.com/janousy)
- Michael Bucher: [mialbu](https://github.com/mialbu)
- Gokila Senthilkumar: [mgoki](https://github.com/mgoki)

## References

1. S. Abbaspour Asadollah, R. Inam, and H. Hansson. A survey on testing for cyber physical system. In K. El-Fakih, G. Barlas, and N. Yevtushenko, editors, Testing Software and Systems, pages 194–207, Cham, 2015\. Springer Intern. Publishing.
2. N. Kalra and S. Paddock. Driving to safety: How many miles of driving would it take to demonstrate autonomous vehicle reliability? Transportation Research Part A: Policy and Practice, 94:182–193, 12 2016.
3. M. Torngren and U. Sellgren. ¨ Complexity Challenges in Development of Cyber-Physical Systems, pages 478–503\. Springer International Publishing, Cham, 2018.
4. D. S. Johnson, H. Koehneman, D. LaFortune, D. Leffingwell, S. Magill, S. Mayner, A. Ofer, R. Stroud, A. Wallgren, and R. Yeman. INDUSTRIAL DEVOPS - Applying DevOps and Continuous Delivery to Significant Cyber-Physical Systems. National Academies Press, 2017
5. Bill Bosshard - Automatically Testing Cyber-physical Systems in Virtual Environments - link to the paper Repository of ML pipeline: <https://github.com/billbos/CPS-SORTER.git> <https://github.com/billbos/CPS-SORTER-JAVA-COMPONENT.git>
