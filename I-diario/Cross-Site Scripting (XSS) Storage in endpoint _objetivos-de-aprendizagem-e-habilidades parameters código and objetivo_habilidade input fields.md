### Summary
The application fails to properly validate and sanatize user supplied input, hence leading to a stored cross-site scripting vulnerability that resides within the _código_ and _objetivo/habilidade_ input fields on [/objetivos-de-aprendizagem-e-habilidades](https://idiario.ieducar.com.br/objetivos-de-aprendizagem-e-habilidades).

### Details
While editing the _código_ and _objetivo/habilidade_ input fields, which can be accessed at BNCC > Objetivos de aprendizagem e habilidades, it's possible to insert arbitrary javascript code which is then stored and executed once the user access the  [History](https://idiario.ieducar.com.br/objetivos-de-aprendizagem-e-habilidades/1402/historico) page.

### PoC
Firstly, the _código_ and _objetivo/habilidade_ field was changed and the payload `"><img src=x onerror=alert('XSS-PoC')>`  was inserted. 

![image](\images\bncc_obj_pay1.png) 

![image](idiario\bncc_obj_pay.png)

![image](idiario\bncc_obj.png)

![image](idiario\bncc_obj_res1.png)

Secondly, once the user access the [History](https://idiario.ieducar.com.br/objetivos-de-aprendizagem-e-habilidades/1402/historico) page the payload was triggered.

![image](idiario\bncc_obj_res.png)

**Affected endpoint =>/objetivos-de-aprendizagem-e-habilidades**
**Affected parameter => Código and Objetivo/Habilidade**

### Impact

- Stealing session cookies: Attackers can use stolen session cookies to hijack a user's session and perform actions on their behalf.
- Downloading malware: Attackers can trick users into downloading and installing malware on their computers.
- Hijacking browsers: Attackers can hijack a user's browser or deliver browser-based exploits.
- Stealing credentials: Attackers can steal a user's credentials.
- Obtaining sensitive information: Attackers can obtain sensitive information stored in a user's account or in their browser.
- Defacing websites: Attackers can deface a website by altering its content.
- Misdirecting users: Attackers can change the instructions given to users who visit the target website, misdirecting their behavior.
- Damaging a business's reputation: Attackers can damage a business's image or spread misinformation by defacing a corporate website.

### Discoverer

([Fernanda Martins](https://github.com/FeMarb/)) (founder)
([Natan Morette](https://br.linkedin.com/in/nmmorette/pt)) (coordinator)

by [CVE-Hunters](https://github.com/Sec-Dojo-Cyber-House/cve-hunters)
