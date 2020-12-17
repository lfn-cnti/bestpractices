# CNF Working Group

## Table of Contents
* [Introduction](#intro)
* [Scope](#scope)
* [Best Practices for CNF Developers](#best_cnf_dev)


<a name="intro"></a>
## Introduction

The goal of this group is to define set of practices in which CNF can be evaluated on to dtermine how cloud native a CNF is (based on those best practices). CNF can be evaluated against those best practices thourhg test cases that are developed by other complimentary open source projects.

The goal of CNF-WG is not trying to define what cloud native for netowrk function is. CNF-WG will rely on other industry inititaves (such as CNCF TUG) to define that.

>> take more about how those best practices can be consumed by the industry (relation to other industry bodies)

>> List other complientary opensource projects.

>> Add Figure here to show the relation btween CNF-WG, CNTT, CNF-Testbed, LFN OVP, etc.

>> Talk about Type for each best practice (MUST, MUST_NOT, SHOULD, SHOULD_NOT)

- **MUST**:
- **MUST NOT**:
- **SHOULD**:
- **SHOULD NOT**:

<a name="scope"></a>
## Scope

As demonstrated by **Figure 1-1** below, When it comes to Cloud Native Network Functions (CNFs), there are many areas that can be foucused on in order to determine different best practices for different Actors. they are:

- **Consumption of CNFs**: Set of best pracitices that helps Customers/Consumers to sonsume and use CNFs in a cloud native way. 
- **Development of CNFs**: Set of best practices that helps CNF Vendors to develop their CNFs in a cloud native way.
- **Operation of CNFs**: Set of best practices that helps CNF Operators to deploy and manage CNFs in a cloud native way.
- **Building of CNF Infrastructure**: Set of best practices that helps CNF Infra Vendors to build and develop CNF Infrastucture in a cloud native way.
- **Operation of CNF Infrastructure**: Set of best practices that helps CNF Infra Operators to deploy and manage CNF infrastucture in cloud native way.

<p align="center"><img src="./figures/cnf-wg-scope.png" alt="scope" title="Scope" width="100%"/></p>
<p align="center"><b>Figure 1-1:</b> Current Scope of CNF-WG</p>

The current focus of CNF-WG is to define the best practices for the Development of CNFs. Other areas are left for future focus.

<a name="Best Practices for CNF Developer"></a>
## Best Practices for CNF Developers

* [Configuration and Lifecycle](./best_cnf_dev.md#1.0)
* [Installable and Upgradeable](./best_cnf_dev.md#2.0)
* [Hardware support](./best_cnf_dev.md#3.0)
* [Microservice](./best_cnf_dev.md#4.0)
* [Compatiblity](./best_cnf_dev.md#5.0)
* [Stateless](./best_cnf_dev.md#6.0)
* [Security](./best_cnf_dev.md#7.0)
* [Scaling](./best_cnf_dev.md#8.0)
* [Observability](./best_cnf_dev.md#9.0)