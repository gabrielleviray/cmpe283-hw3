# Assignment 3

## Team Member
Gabrielle Viray (012340068)

## Prerequisites
Using Assignment 2 environment

## Implementation
1. Modified cpuid.c to include a new leaf (0x4FFFFFFE).
2. Modified vmx.c 
3. Create test program to test CPUID 0x4FFFFFFE.

##Build the Kernel
  - Outer VM: remove previous kvm modules
  ```
  sudo rmmod kvm
  ```
  ```
  sudo rmmod kvm_intel
  ```
  - Compile
  ```
  sudo make -j 8 modules M=arch/x86/kvm
  ```
  - Insert new modules
  ```
  sudo insmod arch/86/kvm/kvm.ko
  ```
  ```
   sudo insmod arch/86/kvm/kvm-intel.ko
  ```
  - Make sure cpuid is installed in inner VM
  - Reboot VM

## Execution
1. Run user mode in inner VM
3. Run test program


## Questions
1. Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail? 
Based on the exit frequency, the rate of exits does not increase at a stable rate. A full VM boot entails about 130,000 exits.

2.Of the exit types defined in the SDM, which are the most frequent? Least? 
Most Frequent:
  Exit Number 1 - External Interrupt
  Exit Number 32 - WRMSR
             
Least Frequent:
  Exit Number 29 - MOV DR
