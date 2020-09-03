# GSoC 2020 Project Report

#### Student: [Bhaskar Kataria](https://gitlab.com/bhaskar792)
#### Mentors: [Tom Henderson](https://gitlab.com/tomhenderson), [Mohit Tahiliani](https://gitlab.com/mohittahiliani), [Vivek jain](https://gitlab.com/Vivek-anand-jain), [Ankit Deepak](https://gitlab.com/adeepkit01)
#### Organisation: [ns-3 Network Simulator](https://www.nsnam.org/)


## Project Overview
For GSoC 2020 with ns-3, I worked on Active Queue Management (AQM) and specifically on developing Low loss low latency, and scalable throughput (L4S) models for various queue disciplines and most of the work is for the traffic-control module of ns-3. L4S is proposed to provide low latency for particular traffic types like video calls, interactive gaming, etc. With the help of the UseL4s attribute, ns-3 users can easily enable L4S and run tests. L4S can now be used with various queue disciplines like CoDel, Cobalt and PIE, and fair queueing versions FqCoDel, FqCobalt, and FqPIE. With the help of these fair queue queue disciplines, seperate queues are created for packets based on various parameters like source, destination, port etc, and because of these seperate queues and L4S, video call and gaming like traffic which does not take up much bandwidth can easily be delivered with low queue delays and hence improving the real time experience for such activities. With the help of example provided or by writing custom scripts, ns-3 users can efficiently work with various scenarios. For verification of the fundamental behavior, unit test cases were also added, and for better understanding, proper documentation was added, which includes the steps to run the tests. The project was divided into 3 phases, and the phase-wise work done is available below.

### Phase 1
After discussing with mentors about the implementation, L4S mode for FqCoDel and CoDel queue disciplines was implemented, and while implementing L4S mode, the same packet getting marked twice issue in CoDel queue discipline was found and resolved. The first phase ended with writing an example script which demonstrates and verifies the L4S mode for FqCoDel queue discipline with TCP DCTCP and TCP Cubic
#### [Download](https://gitlab.com/bhaskar792/ns-3-dev/-/tree/FqCoDel-L4S)
#### Commits
- [traffic-control: Add L4S extensions to FqCoDel and CoDel](https://gitlab.com/nsnam/ns-3-dev/-/commit/b12ac52109c83c1572c73080de21701222b8d7ef)
- [traffic-control: (fixes #225) Do not mark packet twice within a CoDel queue](https://gitlab.com/nsnam/ns-3-dev/-/commit/3caa8e1ec762c93d279ab709e49a53511d675a9c)

### Phase 2
While considering some other options which are available in the documentation, we finally chose to work on FqCobalt which is an essential part of the CAKE module, so in second phase FqCobalt was implemented with complete tests and documentation
#### [Download](https://gitlab.com/bhaskar792/ns-3-dev/-/tree/FqCobalt)

### Phase 3
The third phase included the implementation of FqPIE queue discipline with complete unit test cases and documentation. One minor bug related to multiple bottlenecks was also fixed during this phase, and the patch was provided for previous phases too. During the last week of GSoC, we started writing a document that describes the procedure and results of the test cases required to test the implementation of fair queueing models extensively.
#### [Download](https://gitlab.com/bhaskar792/ns-3-dev/-/tree/FqPIE)

#### Steps to build phase 1
1. Clone ns-3-dev from above provided link
2. Configure ns-3-dev: ./waf configure --enable-tests --enable-examples
3. Build ns-3-dev: ./waf build
4. To run the test suite: ./test.py --suite=fq-codel-queue-disc
5. Run the example program: ./waf --run "fqcodel-l4s-example --scenarioNum=5"

#### Steps to build phase 2
1. Clone ns-3-dev from above provided link
2. Configure ns-3-dev: ./waf configure --enable-tests --enable-examples
3. Build ns-3-dev: ./waf build
4. To run the test suite: ./test.py --suite=fq-cobalt-queue-disc

#### Steps to build phase 3
1. Clone ns-3-dev from above provided link
2. Configure ns-3-dev: ./waf configure --enable-tests --enable-examples
3. Build ns-3-dev: ./waf build
4. To run the test suite: ./test.py --suite=fq-pie-queue-disc

### Possible Extensions
1. Extensive testing of L4S mode and implementation of fair queueing queue disciplines as started in the last week of GSoC.
2. Some possible extensions are available in the documentation of [FqCoDel](https://gitlab.com/bhaskar792/ns-3-dev/-/blob/FqCoDel-L4S/src/traffic-control/doc/fq-codel.rst)

### Online References
#### [Project Wiki](https://www.nsnam.org/wiki/GSOC2020AQM)
#### [Source Code](https://gitlab.com/bhaskar792/ns-3-dev)

### Acknowledgement
I would like to thank all the mentors who helped me with every difficulty I faced with the project and all those extremely good and informational discussions we had, and for providing me the best mentorship, I could have expected. All the guidance and motivation, I got from you all had and will definitely help me in the days to come. It was a great experience working with you.
I would also like to thank Google for providing such a great opportunity.
