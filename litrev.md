What are known vulnerabilities in Kubernetes environments and is there a common denominator between them?
Which concepts recur across the found vulnerabilities and incidents?

Keywords:
Container Security
Container Vulnerability
Kubernetes Security
Kubernetes Vulnerability
Kubernetes Network

Sources: IEEE, CVE, ACM


Thematic outline, split into recurring themes, related to: 

-container level access (non root containers) finding loopholes to execute undesired programs inside the containers
-kubernetes level access (RBAC) finding loopholes to execute undesired requests against the Kubernetes API
-network (networkpolicy) finding loopholes to execute undesired programs inside the containers affecting rest of kubernetes 
infrastructure.


First grand overview, general body
write about red hat survey, incident reports to set the stage
mention larger kubernetes vulnerabilities of the past

explain how I found 3 themes, 

narrow down, analyze each theme with more concrete examples, more precise bodies
for example most recent nginx one's about annotations. Add 2 discussion sentences.


What is a vulnerability? To do so, let’s examine the standard definition from NIST SP 800-53: “A flaw or weakness in system security procedures, design, implementation, or internal controls that could be exercised (accidentally triggered or intentionally exploited) and result in a security breach or a violation of the system(s) security policy.” 

NOTES

https://github.com/kubernetes/ingress-nginx/issues/10571 
and 
https://github.com/kubernetes/ingress-nginx/issues/10572 
state that Multi-tenant environments where non-admin users have permissions to create Ingress objects are most affected by this issue. disc.: This can be attributed to poor access control implementations. It is not necessary for every contributor to a Kubernetes environment to have admin access leve. 

explore the Security Threat Landscape:

LOG4SHELL as example for rootless containers

search for RBAC kubernetes

describe most recent nginx vulns

CVE-2019-5736 CAN BE MITIGATED WITH NON ROOT USER!


Kubernetes uses a container runtime like CRI-O or Docker to safely share each node’s kernel and resources with the various containerized applications running on it. The Linux kernel accepts runtime parameters that control its behavior. Some parameters are namespaced and can therefore be set in a single container without impacting the system at large. Kubernetes and the container runtimes it drives allow pods to update these “safe” kernel settings while blocking access to others. from https://www.crowdstrike.com/blog/cr8escape-new-vulnerability-discovered-in-cri-o-container-engine-cve-2022-0811/

CVE-2022-0811, both rootless container and RBAC


Many things can be done, as low level on the linux vm etc. id like to shift attention to the simple docker and kubernetes part of things. 

Specifically in the
example of CVE-2022-0811, the "kernel.core_pattern" kernel parameter is specified, which controls the kernel's reaction to a core dump. If a core dump is done 
in a CRI-O container, the parameter states the execution of a malicious binary in the root context of the container, on the host. 
the foundation of such attacks is being able to either freely instantiate containers or freely move and operate from inside a container. 





