# Security Lab: System Hardening

## Objective
- Patch Linux instances using default baseline
- Create custom patch baseline 
- Use patch groups to to patch Windows instances using custom patch baseline 
- Verify patch compliance

## Steps Taken
The lab was broken down into four phases using a preconfigured environment with three Linux and three Windows EC2 instances.

#### Part 1: Patching Linux Instances with Default Baseline

1. Accessed the Patch Manager feature within AWS Systems Manager.
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 125855.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 125937.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 130203.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 130219.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 130357.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 130533.png>)

2. Click the *Patch now* option in the Patch Manager window  
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 130755.png>)

3. Set the Patching operation to *Scan and install* and the Reboot option to *Reboot if needed*.
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 131056.png>)

4. Selected *Specify instance tags* and used the tag `Patch Group` with the value `LinuxProd` to target the three Linux instances.
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 131205.png>)

5. Scroll down and click the *Patch now* button to apply the default baseline (`AWS-AmazonLinux2DefaultPatchBaseline`).
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 131243.png>)

5. Executed the patch command and monitored the status until the operation completed successfully on all three Linux instances.
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 132606.png>)

#### Part 2: Creating a Custom Patch Baseline for Windows

1. Created a new patch baseline named `WindowsServerSecurityUpdates` for the *Windows* Operating system.
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 132913.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 133319.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 133747.png>) 

![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 134228.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 134420.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 134452.png>)

2. Added an approval rule for **WindowsServer2019** that targeted patches with *Severity* *Critical* and *Classification* *SecurityUpdates*, setting "Auto-approval" to *3 days*.
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 134214.png>) 

3. Added a second rule for **WindowsServer2019** that targeted patches with *Severity*, *Important*, and *Classification* *SecurityUpdates*, setting "Auto-approval" to *3 days*.

4. Modified the new `WindowsServerSecurityUpdates` baseline to associate it with the patch group named `WindowsProd`.


#### Part 3: Tagging and Patching Windows Instances

1. Used the EC2 console to add a tag with *Key:* *Patch Group* and *Value:* *WindowsProd* to all three Windows instances (`Windows-1`, `Windows-2`, and `Windows-3`).
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 140612.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 140700.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 140744.png>) 
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 140827.png>) 
  
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 141258.png>)

2. Returned to Patch Manager and chose *Patch now*.


3. Used the same configuration as Phase 1 (*Scan and install*, *Reboot if needed*) but targeted the tag *Key:* *Patch Group* with *Value:* *WindowsProd*.


4. Executed the patch command, and monitored the output in the Run Command section, which showed Patch Manager using the Run Command to run the patching operations based on the defined `WindowsProd` patch group.


#### Part 4: Verifying Compliance

1. Navigated to the Patch Manager Dashboard tab and confirmed that the *Compliance summary* showed *Compliant*, verifying all three Linux and all three Windows instances were compliant.
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 141814.png>)

2. Checked the *Compliance reporting* tab to verify the *Compliance status* was *Compliant* for all six instances and reviewed details like the baseline used and the specific patches applied to the Windows nodes.
![alt text](<images/System-Hardening Lab/Screenshot 2025-11-26 142030.png>)

## Challenges
- 

## Takeaways

The single most important lesson is that trying to manually patch hundreds or thousands of servers is time consuming and impossible. Patch Manager provides the necessary automation to maintain security standards across the entire fleet from a single console.

The ability to create a *custom patch baseline* (Phase 2) is crucial. It shows that organizations don't have to install every single patch; they can enforce a specific security policy, such as only approving Critical and Important security updates, and reject other less urgent updates.

Making use of *patch groups* via EC2 tags (e.g., `LinuxProd`, `WindowsProd`) is an effective way to organize and target specific environments. This ensures the right patches are applied to the right servers (e.g., Linux gets the default baseline, Windows gets the security-focused custom baseline).

And finally, patching is incomplete without *verification*. The Patch Manager Dashboard provides the immediate, auditable proof that the security policy was successfully enforced across the entire environment.
