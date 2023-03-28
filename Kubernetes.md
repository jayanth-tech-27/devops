pod level issues 
----------------
* node dosn't have suffisient memory
* 
1. image pullbackof
--------------------

 * resons:
    * invalid image
    * invalid tag
    * invalid permissions
```
2. for trubulshooting i aws used `kubernetis cheat sheet `as a gu(referece purpus)
  * kubectl describe---> its shoes the all info of pod,rs,svc,diployment pod ....ect)
  * kub ctl logs
```  
3. image pulled but pod is pending
-----------------------------------

 * resons:
    * resourcesqota on namespace
    * Request and limit set
    * node or nodes lack of resources
    * also , check the kube-scheduler component
    * kube ctl events command --> its show the all the dat about pod,rs,svc,diployment pod ....ect)
```
name spaces:
* isolated aria
* we canot use resorces to one name space to onther one (every ns has have there alocated resorces)
* logical sparation taken care by the name spases
```
4. crashloopbackoff
--------------------
* resons:
    * liveness probe failure
    * application faild to start for any reson
    * the application run time was not working
    * the application was running but is write to  folder dosnot exits and don't have permissions

5. image pulled but pod is not ready:
-------------------------------------
* always check for the Readiness probes.
6. out of memory (OOM):
-----------------------
* this error is catogarised in two tyoes:
   * **oom killed: limit overcommit**
      * the error occurs when some of the pods limits is greter than the available memory in the pod  
   * **oom killed: container limt reached**
     * this erroe eccors a pod is using more momory then the set limit 
* resons:
     * 
  * pod is running out of memory then the alocated the memory by resourece kota administator.( he does alocated the resouece for evry namespaces)

6.  to get prosessid --> **loging to the container or pod and execute `ps-ef'**




