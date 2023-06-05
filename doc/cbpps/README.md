# CNF Best Practice Proposal (CBPP)

A  CNF Best Practice Proposal (CBPP) is a way to propose, communicate and coordinate on new best practices for the CNF WG. You can read the full details of the project in [CBPP-1](0001-cnf-best-practice-proposal-process.md)

This process is still in an alpha state and feedback is welcome.

## Quick start for the CBPP process

Follow the process outlined in the [CBPP process document](cnf_best_practice_process.md).

## CNF Use Cases

CBPP shall always refer to at least one of the CNF WG use cases. Those use cases serve as the practical and concrete basis for deriving, discussing and evaluating the best practices for CNFs. Their value is in providing context and a reality check for CBPPs. With help of use cases we make sure that CBPPs are addressing a specific problem or need from the real world. Please use the [Use Case Template](../doc/use-case/NNNN-UC-template.md) to contribute a use case.

## Using best practices

CNFs should be compliant with applicable best practices, and ops processes
should be validated for compliance with them.  However, compliance is a
journey, and we expect end users to start with little compliance and
improve over time.  The [CBPP-3](0003-exceptions.md) discusses how you should
document your compliance and any places where you require an exception for
being non-compliant.  This allows any auditor (e.g. a consumer of your CNF,
your security group, an external auditing entity) to determine where you
are not following best practices, _why_ you are not following best practices,
whether you have mitigations in place for any risks this may cause, and
whether this is acceptable to them.

If your team builds a component used in NFV, or operates a component of
NFV, CBPP-3 explains how you document your compliance status.  We recommend
you make this best practice a part of your delivery process.
