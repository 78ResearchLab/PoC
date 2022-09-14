```
(128.414): Access violation - code c0000005 (first chance)
First chance exceptions are reported before any exception handling.
This exception may be expected and handled.
ikeext!IkeQueueRecvRequest+0x158:
00007ffb`9e48d138 0f1000          movups  xmm0,xmmword ptr [rax] ds:0000017a`08459000=????????????????????????????????

0:005> r
rax=0000017a08459000 rbx=0000000000000000 rcx=00000008905fef70
rdx=ffffffffffffc000 rsi=00000008905feff0 rdi=0000017a08456f10
rip=00007ffb9e48d138 rsp=00000008905fef30 rbp=00000008905fefa0
 r8=0000000000000000  r9=0000000000000000 r10=0000017a08459000
r11=0000017a08459000 r12=0000000000000000 r13=0000017a0843cb80
r14=0000017a08456f20 r15=0000000000000001
iopl=0         nv up ei pl zr na po nc
cs=0033  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00010246
ikeext!IkeQueueRecvRequest+0x158:
00007ffb`9e48d138 0f1000          movups  xmm0,xmmword ptr [rax] ds:0000017a`08459000=????????????????????????????????

0:005> !heap -p -a @rax
    address 0000017a08459000 found in
    _DPH_HEAP_ROOT @ 17a08281000
    in busy allocation (  DPH_HEAP_BLOCK:         UserAddr         UserSize -         VirtAddr         VirtSize)
                             17a08285a28:      17a08459000                0 -      17a08458000             2000
ReadMemory error for address 0000017a08459000
    00007ffbc8177e7f ntdll!RtlDebugAllocateHeap+0x000000000000003f
    00007ffbc811e1fa ntdll!RtlpAllocateHeap+0x000000000009c70a
    00007ffbc807fcad ntdll!RtlpAllocateHeapInternal+0x000000000000098d
    00007ffb9e486910 ikeext!WfpMemAlloc+0x0000000000000020
    00007ffb9e48d0ce ikeext!IkeQueueRecvRequest+0x00000000000000ee
    00007ffb9e4f1c0d ikeext!IkeReinjectReassembledPacket+0x0000000000000181
    00007ffb9e4f17ed ikeext!IkeInsertFragEntry+0x0000000000000259
    00007ffb9e4f1865 ikeext!IkePostPayloadProcessFrag+0x0000000000000031
    00007ffb9e4f1564 ikeext!IkeHandlePayloadFrag+0x00000000000000ac
    00007ffb9e507652 ikeext!IkeHandleMMPacketDispatchAuthip+0x000000000000005e
    00007ffb9e4ead86 ikeext!IkeProcessPacket+0x00000000000002f2
    00007ffb9e47fc84 ikeext!IkeProcessPacketDispatch+0x0000000000000fd4
    00007ffb9e47bb9c ikeext!IkeHandleRecvRequest+0x000000000000000c
    00007ffbc809e7e9 ntdll!TppSimplepExecuteCallback+0x0000000000000099
    00007ffbc8086964 ntdll!TppWorkerThread+0x0000000000000644
    00007ffbc7cc7974 KERNEL32!BaseThreadInitThunk+0x0000000000000014
    00007ffbc80ca2f1 ntdll!RtlUserThreadStart+0x0000000000000021

 
0:005> dq @rax
0000017a`08459000  ????????`???????? ????????`????????
0000017a`08459010  ????????`???????? ????????`????????
0000017a`08459020  ????????`???????? ????????`????????
0000017a`08459030  ????????`???????? ????????`????????
0000017a`08459040  ????????`???????? ????????`????????
0000017a`08459050  ????????`???????? ????????`????????
0000017a`08459060  ????????`???????? ????????`????????
0000017a`08459070  ????????`???????? ????????`????????

0:005> k
 # Child-SP          RetAddr               Call Site
00 00000008`905fef30 00007ffb`9e4f1c0d     ikeext!IkeQueueRecvRequest+0x158
01 00000008`905fefd0 00007ffb`9e4f17ed     ikeext!IkeReinjectReassembledPacket+0x181
02 00000008`905ff110 00007ffb`9e4f1865     ikeext!IkeInsertFragEntry+0x259
03 00000008`905ff180 00007ffb`9e4f1564     ikeext!IkePostPayloadProcessFrag+0x31
04 00000008`905ff1c0 00007ffb`9e507652     ikeext!IkeHandlePayloadFrag+0xac
05 00000008`905ff200 00007ffb`9e4ead86     ikeext!IkeHandleMMPacketDispatchAuthip+0x5e
06 00000008`905ff230 00007ffb`9e47fc84     ikeext!IkeProcessPacket+0x2f2
07 00000008`905ff2f0 00007ffb`9e47bb9c     ikeext!IkeProcessPacketDispatch+0xfd4
08 00000008`905ff850 00007ffb`c809e7e9     ikeext!IkeHandleRecvRequest+0xc
09 00000008`905ff880 00007ffb`c8086964     ntdll!TppSimplepExecuteCallback+0x99
0a 00000008`905ff8d0 00007ffb`c7cc7974     ntdll!TppWorkerThread+0x644
0b 00000008`905ffbc0 00007ffb`c80ca2f1     KERNEL32!BaseThreadInitThunk+0x14
0c 00000008`905ffbf0 00000000`00000000     ntdll!RtlUserThreadStart+0x21
```
