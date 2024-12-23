# AP-Isolation-Bypass
校园网AP隔离解决方案-解决校内设备无法互相通信的臭毛病

# exe使用方法
双击运行，自动检测网卡阶段可能需要按一下回车，成功自动配置路由表后程序会自动关闭
每次重新联网或者重启电脑需要重新运行一次AP隔离破解的exe

# 我们的目标是解决校内两设备无法互相通信的臭毛病
# 核心思想，自己重新设置路由规则
举个例子
- AP隔离就像"教室规定学生不能直接传纸条"
- 但学生都可以和老师（网关）通信
- 修改路由相当于"所有纸条都先交给老师转交"
- 这样就绕过了"学生之间不能直接传纸条"的限制

# 问题介绍 AC AP 隔离
两台电脑在同一楼层时触发了ap隔离，但是隔了距离跨ap是可以正常访问的，这就是原因

>AP隔离非常类似有线网络的VLAN(虚拟局域网)，将所有的无线客户端设备之间完全隔离，是客户端只能访问AP接入的固定网络。通俗来讲，就是各个连接无线的客户机（如手机、电脑等）之间无法互相通讯的，即你无法在两台同时连接AP的电脑间使用类似共享文件等功能。因此，在开启该功能之后，可以保护不同用户间的数据安全，有利于抵御外部攻击。

# 让我用简单的方式解释AP隔离破解的原理：

1. 正常情况（有AP隔离）
	- AP隔离阻止了同一AP下设备之间的直接通信
	- 但所有设备都能和网关通信
```
设备A ←→ AP ←→ 设备B
        ❌
设备A ←→ 设备B
```


2. 修改路由后：
	- 删除直连路由，强制所有通信都经过网关
	- 网关成为"中转站"，帮助转发数据包
```
设备A → 网关 → 设备B
设备B → 网关 → 设备A
```

3. 具体原理：
	- 默认路由表让设备尝试在同一网段内直接通信
	- AP隔离阻止了这种直接通信
	- 修改路由后，即使是同网段通信也会发送到网关
	- 网关没有AP隔离限制，可以转发到目标设备

**就像**：
- AP隔离就像"教室规定学生不能直接传纸条"
- 但学生都可以和老师（网关）通信
- 修改路由相当于"所有纸条都先交给老师转交"
- 这样就绕过了"学生之间不能直接传纸条"的限制

# 破解工作原理

```
设备A ─→ 检测网关 ─→ 修改路由 ─┐
	                        ├─→ 可以互相访问
设备B ─→ 检测网关 ─→ 修改路由 ─┘
```


# AP-Isolation-Bypass
Campus Network AP Isolation Solution - Solving the annoying problem of devices unable to communicate with each other within campus

# How to Use the Exe
Double-click to run. During automatic network card detection, you may need to press Enter. The program will automatically close after successfully configuring the routing table.
You need to run the AP isolation bypass exe again every time you reconnect to the network or restart your computer.

# Our Goal is to Solve the Problem of Two Devices Unable to Communicate Within Campus
# Core Concept: Resetting Routing Rules Ourselves
For example:
- AP isolation is like "classroom rules prohibiting students from passing notes directly"
- But all students can communicate with the teacher (gateway)
- Modifying routes is equivalent to "having all notes passed through the teacher"
- This bypasses the restriction of "students cannot pass notes directly"

# Problem Introduction: AC AP Isolation
When two computers are on the same floor, AP isolation is triggered, but normal access is possible when they are separated across different APs.

>AP isolation is very similar to VLAN (Virtual Local Area Network) in wired networks. It completely isolates all wireless client devices from each other, allowing clients to only access the fixed network connected to the AP. In simple terms, this means connected wireless clients (such as phones, computers, etc.) cannot communicate with each other, preventing functions like file sharing between two computers connected to the same AP. Therefore, enabling this feature protects data security between different users and helps resist external attacks.

# Let me explain the principle of AP isolation bypass in simple terms:

1. Normal situation (with AP isolation)
    - AP isolation prevents direct communication between devices under the same AP
    - But all devices can communicate with the gateway
  
```
Device A ←→ AP ←→ Device B
❌
Device A ←→ Device B
```

2. After route modification:
    - Delete direct routes, force all communication through gateway
    - Gateway becomes a "relay station" to help forward data packets
  

```
Device A → Gateway → Device B
Device B → Gateway → Device A
```


3. Specific principle:
    - Default routing table makes devices try to communicate directly within the same network segment
    - AP isolation prevents this direct communication
    - After route modification, even same-segment communication goes through the gateway
    - Gateway has no AP isolation restrictions and can forward to target devices

**It's like**:
- AP isolation is like "classroom rules prohibiting students from passing notes directly"
- But all students can communicate with the teacher (gateway)
- Modifying routes is equivalent to "having all notes passed through the teacher"
- This bypasses the restriction of "students cannot pass notes directly"

# How the Bypass Works


```
Device A ─→ Detect Gateway ─→ Modify Routes ─┐
					     ├─→ Can access each other
Device B ─→ Detect Gateway ─→ Modify Routes ─┘
```
