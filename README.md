# MATLAB_crack version R2022b

Matlab license system is based on FlexLm that is implemented in:
\MATLAB\R2022b\bin\win64\matlab_startup_plugins\lmgrimpl\libmwlmgrimpl.dll

1. Get trial license of MATLAB
2. Install all toolbox components
3. Make a patch of libmwlmgrimpl.dll in places:
```
HWID
00007FFB260D111D   | E8 CEBBFFFF                     | call libmwlmgrimpl.7FFB260CCCF0                    |
00007FFB260D1122   | 85C0                            | test eax,eax                                       |
00007FFB260D1124   | 0F85 C5000000                   | jne libmwlmgrimpl.7FFB260D11EF                     |
00007FFB260D112A   | 8BFB                            | mov edi,ebx                                        |
00007FFB260D112C   | E9 BE000000                     | jmp libmwlmgrimpl.7FFB260D11EF                     |
00007FFB260D1131   | 4C:8D46 08                      | lea r8,qword ptr ds:[rsi+8]                        | r8:"7A16F9E8:736C61766563", rsi+8:"7A16F9E8:736C61766563"
00007FFB260D1135   | 48:8D55 08                      | lea rdx,qword ptr ss:[rbp+8]                       |
00007FFB260D1139   | 49:8BCE                         | mov rcx,r14                                        |
00007FFB260D113C   | E8 BF010000                     | call libmwlmgrimpl.7FFB260D1300                    |
00007FFB260D1141   | 85C0                            | test eax,eax                                       | test HWID
00007FFB260D1143   | 0F84 A6000000                   | je libmwlmgrimpl.7FFB260D11EF  <--- PUT NOPs here                    |
00007FFB260D1149   | BF 01000000                     | mov edi,1                                          |
00007FFB260D114E   | E9 9C000000                     | jmp libmwlmgrimpl.7FFB260D11EF                     |
00007FFB260D1153   | BB 01000000                     | mov ebx,1                                          |
00007FFB260D1158   | 66:83FA 18                      | cmp dx,18                                          |
00007FFB260D115C   | 75 05                           | jne libmwlmgrimpl.7FFB260D1163                     |
00007FFB260D115E   | 44:8BCB                         | mov r9d,ebx                                        |
00007FFB260D1161   | EB 0F                           | jmp libmwlmgrimpl.7FFB260D1172                     |
00007FFB260D1163   | 66:83FA 19                      | cmp dx,19                                          |
00007FFB260D1167   | 44:8BCF                         | mov r9d,edi                                        |
00007FFB260D116A   | 41:0F95C1                       | setne r9b                                          |
```
```
SIGNATURE
-----------------------
00007FFB29CAF95A   | E8 F1DD0700                     | call libmwlmgrimpl.7FFB29D2D750                    |
00007FFB29CAF95F   | 85C0                            | test eax,eax                                       |
00007FFB29CAF961   | 74 0D                           | je libmwlmgrimpl.7FFB29CAF970                      |
00007FFB29CAF963   | 44:8BC0                         | mov r8d,eax                                        |
00007FFB29CAF966   | BA 30290000                     | mov edx,2930                                       |
00007FFB29CAF96B   | E9 C2FEFFFF                     | jmp libmwlmgrimpl.7FFB29CAF832                     |
00007FFB29CAF970   | 396C24 44                       | cmp dword ptr ss:[rsp+44],ebp                      |
00007FFB29CAF974   | 75 3B                           | jne libmwlmgrimpl.7FFB29CAF9B1  <------- put JMP here                   |
00007FFB29CAF976   | 45:33C9                         | xor r9d,r9d                                        |
00007FFB29CAF979   | 48:896C24 30                    | mov qword ptr ss:[rsp+30],rbp                      |
00007FFB29CAF97E   | 41:B8 14020000                  | mov r8d,214                                        |
00007FFB29CAF984   | 41:8D51 F8                      | lea edx,qword ptr ds:[r9-8]                        |
00007FFB29CAF988   | 48:8BCF                         | mov rcx,rdi                                        |
00007FFB29CAF98B   | C74424 28 FF000000              | mov dword ptr ss:[rsp+28],FF                       |
00007FFB29CAF993   | C787 88000000 F8FFFFFF          | mov dword ptr ds:[rdi+88],FFFFFFF8                 |
00007FFB29CAF99D   | 48:896C24 20                    | mov qword ptr ss:[rsp+20],rbp                      |
00007FFB29CAF9A2   | E8 D9D5FFFF                     | call libmwlmgrimpl.7FFB29CACF80                    |
00007FFB29CAF9A7   | B8 F8FFFFFF                     | mov eax,FFFFFFF8                                   |
00007FFB29CAF9AC   | E9 8EFEFFFF                     | jmp libmwlmgrimpl.7FFB29CAF83F                     |
00007FFB29CAF9B1   | 33C0                            | xor eax,eax                                        |
00007FFB29CAF9B3   | E9 87FEFFFF                     | jmp libmwlmgrimpl.7FFB29CAF83F                     |
```

4. Now you can edit Your license file and extend trial perion and move to another machine
5. done