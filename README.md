# Problem I have

When I generate the dump.o object from the interop project, it looks like I am missing some definitions (in `undefined.txt`), e.g.,:

```

                 U _ZSt3getILm0EJPN7sandbox20ExportedFunctionBaseESt14default_deleteIS1_EEERKNSt13tuple_elementIXT_ESt5tupleIJDpT0_EEE4typeERKS9_
                 U _ZSt3getILm0EJPN7sandbox20ExportedFunctionBaseESt14default_deleteIS1_EEERNSt13tuple_elementIXT_ESt5tupleIJDpT0_EEE4typeERS9_
                 U _ZSt3getILm0EJPN7sandbox8platform20SharedMemoryMapPOSIXINS1_6detail23SharedMemoryObjectPOSIXEEESt14default_deleteIS5_EEERNSt13tuple_elementIXT_ESt5tupleIJDpT0_EEE4typeERSD_
                 U _ZSt3getILm1EJPN7sandbox8platform20SharedMemoryMapPOSIXINS1_6detail23SharedMemoryObjectPOSIXEEESt14default_deleteIS5_EEERNSt13tuple_elementIXT_ESt5tupleIJDpT0_EEE4typeERSD_
                 U _ZSt3maxImERKT_S2_S2_
                 U _ZSt3minImERKT_S2_S2_
                 U _ZSt4moveIRPN7sandbox8platform20SharedMemoryMapPOSIXINS1_6detail23SharedMemoryObjectPOSIXEEEEONSt16remove_referenceIT_E4typeEOS9_
                 U _ZSt5applyIRPFivERSt5tupleIJEEEDcOT_OT0_
                 U _ZSt5applyIRPFPciERSt5tupleIJiEEEDcOT_OT0_
                 U _ZSt7forwardIPN7sandbox16ExportedFunctionIiJEEEEOT_RNSt16remove_referenceIS4_E4typeE
                 U _ZSt7forwardIPN7sandbox16ExportedFunctionIPcJiEEEEOT_RNSt16remove_referenceIS5_E4typeE
                 U _ZSt8_DestroyIPSt10unique_ptrIN7sandbox20ExportedFunctionBaseESt14default_deleteIS2_EES5_EvT_S7_RSaIT0_E

```

In the LLVM IR `dump.txt`, these seem to be declared but not defined.
If we compare with the `.o` generated for the `process_sandbox`::`sandboxed-basic`, the same symbols are defined as weak (`nm` gives a `W`) but exist in both the `.o` and the `.so`.

Thus: Why is interop not generating the code for these functions? Or did I not look correctly?

