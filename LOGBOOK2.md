
# Trabalho realizado nas Semanas #2 e #3

## Identificação

CVE-2024-47066 ( https://github.com/lobehub/lobe-chat/security/advisories/GHSA-3fc8-2r3f-8wrg )
Esta vulnerabilidade é pertencente ao projeto lobechat (https://github.com/lobehub/lobe-chat , website lobechat.com), que já tinha tido outra vulnerabilidade de Server-Side Request Forgery (SSRF) divulgada em 10/05/2024 (CVE-2024-32964: https://github.com/lobehub/lobe-chat/security/advisories/GHSA-mxhq-xw3g-rphc ) e cujo arranjo não foi suficiente, levando à descoberta desta vulnerabilidade também de SSRF.

## Catalogação

Divulgado em 21/09/2024 e descoberto por a1loy ( https://github.com/a1loy ). Este CVE está ligado ao CWE-918: Server-Side Request Forgery (SSRF) foi classificado com o nível 8.8 (high) atualizado a 30/09/2024 na escala de CVSS (Common Vulnerability Scoring System). (https://nvd.nist.gov/vuln/detail/CVE-2024-47066 )

Nota:

Visto que o projeto é open source, bastante “popular” no github e como não encontrámos nenhuma informação sobre o porquê de ter sido descoberto, nem nenhum relato de ataque nocivo, só que aviso público e que a vulnerabilidade só foi feita pública através do GitHub Advisory Database na secção revista pelo GitHub (https://github.com/advisories/GHSA-3fc8-2r3f-8wrg ) a 21/09/2024, acreditamos que a1loy tenha simplesmente encontrado e reportado a vulnerabilidade aos responsáveis do projeto.

## Exploit

Esta vulnerabilidade de Server-Side Request Forgery (SSRF) ocorre porque as proteções contra a mesma não estavam a considerar redirect e podia ser ultrapassada com a utilização de um URL malicioso que redireciona para um recurso privado.
Como na demonstração (https://github.com/l8BL/CVE-2024-47066 ) em que o atacante usa um encurtador de URL e a função para determinar se o endereço leva a algum endereço privado (isPrivate()) consegue ser ultrapassada.

## Ataques

Não existem nenhuns relatos da vulnerabilidade ter sido usada em algum ataque, no entanto dada a simplicidade de explorar a vulnerabilidade, não serem necessários privilégios para a utilizar, assim como o acesso interno que fornece, esta vulnerabilidade poderia levar a um ataque teria um impacto alto em termos de confidencialidade, disponibilidade. A nível de integridade encontrámos várias fontes conflituosas. (https://github.com/advisories/GHSA-3fc8-2r3f-8wrg , https://nvd.nist.gov/vuln/detail/CVE-2024-47066 )
