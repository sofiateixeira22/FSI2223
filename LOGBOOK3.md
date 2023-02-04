
# Trabalho realizado na Semana #3

## Identification

- The vulnerabily chosen by the group is CVE-2018-17707.
- This vulnerability happened to vendor Epic Games, affecting their product Epic Games Launcher.
- It's weakness enumeration is CWE-78, which refers to Improper Neutralization of Special Elements used in an OS Command.
- It was fixed in version 8.2.2 of Epic Games Launcher.

## Cataloging

- It was originally scored by CVSS 2.0, having a score of 6.8 (medium).
- When the CVSS 3.x Severity and Metrics was introduced, the score increased to 8.8 (high).
- Reported by Andrea Micalizzi, AKA rgod from 9sg security team on 14-09-2018 as a part of the vendors bug-bounty program.
- They offered between 1000$ and 3000$ on 2.0 Version. Finally offered 5000$ to 10000$ on 3.0 Version according to their program.

## Exploit

- The specific flaw exists within the handler for the com.epicgames.launcher protocol.
- To exploit this vulnerability it's required user interaction so that the target must visit/open a malicious page/file.
- A crafted URI with the com.epicgames.launcher protocol can trigger execution of a system call composed from a user-supplied string.
- This exploit takes advantage of OS Command Injection that allows attackers to execute unexpected, dangerous commands directly on the OS.

## Attacks

- This allows remote attackers to take advantage of vulnerable installations of Microsoft Visual Studio with Unreal Engine development tools installed.
- An attacker can leverage this vulnerability to execute code in the context of the current user.
- Attackers could execute unauthorized commands, used to disable the software/read and modify data that the attacker hasn't direct access permissions.
- The product is directly executing commands instead of the attacker, malicious activities appear to come from the application/application's owner.