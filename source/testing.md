# Testing spec files

Here are the steps we do when we test a spec file

1. We build a Source RPM

    The Source RPM (SRPM) is built on a fresh machine, then it is fetched in the
    Jenkins workspace.

1. We make a scratch build on CBS

    Scratch builds allows us to ensure that the spec file is correct. It does
    not help us to make a good package, because scratch builds do not rebuild
    the SRPM first ([source][1]).

1. We change the Release and Provides in the spec file

    We change the spec file in order to be able to publish the RPM in koji. We
    use the Jenkins build number and pull request as identifier (release field).
    That ensures that we can rebuild the same pull request multiples times
    without the need to change the release first.

    Also, it makes it clear that the package is made out of a pull request and is
    not a final rpm.

1. We make a candidate build -- identified by the Jenkins job numer and pull
   request id.

    The candidate build has several advantages:

    - At that time, the SRPM itself is rebuild.
    - Inside the job, we can do "yum install package-pull-request(pull request
      id and job id). That way, we know that we fetch exactly the package that
      we need.

[1]:https://fedoraproject.org/wiki/Using_the_Koji_build_system#Scratch_Builds
