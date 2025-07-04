--- 
front: 
hard: Advanced 
time: 15 minutes 
--- 

# Version management suggestions 

## Overview 
Version management refers to the management of changes to various program codes, configuration files, and documentation files during software development. 
The main function of version management is to track file changes. It faithfully records information such as when and who changed what content in the file. 
### Necessity of version management tools 
- Version management tools are indispensable for multi-person team development, and are the basis for achieving parallel development and improving development efficiency of the development team 
- Version management tools provide effective tracking methods for the development process of files or directories in the software development process, ensuring that they can return to the old version when needed, avoiding the loss of files, loss of modifications and mutual overwriting 
- Version management tools prevent unauthorized access and modification through access control of the version library, effectively protecting enterprise software assets and intellectual property rights 

### Comparison of commonly used version management tools 
- Generally, the most commonly used free version management tools are SVN and GIT 
- SVN is a centralized version control tool 
- GIT is a distributed version control tool 
### Advantages and disadvantages of SVN 
- Advantage 1: Centralized management, the management method is configured on the server side, and the client only needs to submit synchronously. It is easy to use, simple to operate, and easy to get started. 
- Advantage 2: Unified control of access rights on the server side, using code security management. 
- Advantage 3: All codes are based on the server side, and the code consistency is high.
- Disadvantage 1: All operations need to be synchronized through the server, which will lead to higher server performance requirements. If the server is down, the code cannot be submitted. 
- Disadvantage 2: Branch management is not flexible. The SVN branch is a complete directory, and this directory has complete actual files. These operations are synchronized on the server, not localized operations. If you want to delete a branch, you also need to delete the remote branch, which will cause everyone to synchronize. 
- Disadvantage 3: Networking is required. If you cannot connect to the SVN server, you cannot submit your own code, let alone restore, compare and other operations. If it is in the intranet, the network speed is relatively stable and the synchronization is relatively fast. If it is synchronized through the external network, it may take a long time to synchronize. 
- Disadvantage 4: The team needs to create and manage the code repository by themselves, which has a certain threshold 
### Advantages and Disadvantages of GIT 
- Advantage 1: In distributed development, you can git clone a local version, and then perform operations and submit locally. A complete version control can be completed locally. When publishing, use git push to push to the remote. 
- Advantage 2: The essence of git branch is a pointer to the commit snapshot, which is fast and flexible, and branches can be switched at will. All operations can be performed locally without synchronization to the remote. 
- Advantage 3: Conflict resolution. Conflicts can easily occur when multiple people are developing. You can pull the remote to the local first, then merge the branches locally, resolve the conflicts, and then push to the remote. 
- Advantage 4: Offline work. If there is a problem with the git server, you can also switch branches locally, and then submit, merge, and perform other operations after connecting to the network. 
- Disadvantage 1: git does not have strict permission control. Generally, permission control is performed by setting the read and write permissions of the file through the system. 
- Disadvantage 2: The working directory can only be the entire directory, while svn can checkout a directory with permissions separately. 
- Disadvantage 3: git is difficult to use, and the learning cost for pure users is relatively high compared to svn. 

### Recommendation 
- For new teams, it is recommended to use GIT for code version management, and use Gitee instead of Github as the remote code repository 

## Use GIT to manage code 
### Download and install GIT 
- Step 1: Download the git command line: Go to [git official site](https://git-scm.com/downloads), and download the corresponding command line tool according to your system version 
- Step 2: Download the tortoisegit visualization tool: Go to [tortoisegit official site](https://tortoisegit.org/download/), and download the corresponding visualization tool according to your system version 
- Step 3: Download the Chinese language pack of the tortoisegit visualization tool: Go to [tortoisegit official site](https://tortoisegit.org/download/), and download the Simplified Chinese Language Packs 
- Step 4: Follow the instructions to install the programs downloaded from step 1 to step 3 
### Installation and usage instructions 
- Article: [Using Gitee [Code management](https://blog.csdn.net/baiketeam/article/details/82955848) 
- Article: [TortoiseGit installation and configuration](https://www.cnblogs.com/xiuxingzhe/p/9312929.html)

- B station video: [GIT video tutorial (combined with github, code cloud) (no nonsense version)](https://www.bilibili.com/video/BV1LZ4y1W7Ld?from=search&seid=9689408860061067375) 
- B station video: [Silicon Valley GitHub tutorial](https://www.bilibili.com/video/BV1pW411A7a5?from=search&seid=4400489830029833022) 
