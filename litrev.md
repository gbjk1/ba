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






