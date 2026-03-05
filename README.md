# Guia de Configuração de Bloqueio de Sites por Grupo de IP
## Roteador TP-Link ER605

---

## 1. Acessando o Roteador

1. Abra o navegador e digite o endereço IP do roteador (padrão: `192.168.0.1` ou o IP configurado)
2. Faça login com nome de usuário e senha de administrador

---

## 2. Configuração da Rede LAN

### 2.1. Verificar/Criar Rede LAN

**Menu:** `Network > LAN > LAN`

| Campo | Valor |
|-------|-------|
| **IP Address** | 192.168.10.1 |
| **Subnet Mask** | 255.255.255.0 |
| **Profile Status** | normal |
| **802.1d Tag** | 1 |

### 2.2. Configurar Servidor DHCP

**Menu:** `Network > LAN > DHCP Server` (na mesma tela da LAN)

| Campo | Valor |
|-------|-------|
| **DHCP Server** | Enable |
| **Start IP Address** | 192.168.10.100 |
| **End IP Address** | 192.168.10.199 |
| **Lease Time** | 120 minutos |

### 2.3. Importar Reservas de Endereço (Address Reservation)

**Menu:** `Network > LAN > Address Reservation`

1. Clique em **Import**
2. Selecione o arquivo `Address_Reservation_List-2026-03-04-10-08.csv`
3. Clique em **Save**

> **Nota:** As reservas de endereço garantem que dispositivos específicos sempre recebam o mesmo IP, facilitando a aplicação das regras de bloqueio por grupo.

---

## 3. Configuração dos Grupos de IP

### 3.1. Definir os Intervalos de Endereços IP

**Menu:** `Preferences > IP Group > IP Address`

#### Grupo: DESKTOPs_101_a_119

| Campo | Valor |
|-------|-------|
| **Name** | DESKTOPs_101_a_119 |
| **Type** | IP Address Range |
| **Start IP Address** | 192.168.10.101 |
| **End IP Address** | 192.168.10.119 |

#### Grupo: DESKTOP_120

| Campo | Valor |
|-------|-------|
| **Name** | DESKTOP_120 |
| **Type** | IP Address Range |
| **Start IP Address** | 192.168.10.120 |
| **End IP Address** | 192.168.10.120 |

**Para cada grupo:**
1. Clique em **Add**
2. Preencha os campos conforme a tabela acima
3. Clique em **OK**

### 3.2. Criar os Grupos de IP

**Menu:** `Preferences > IP Group > IP Group`

#### Criar Grupo: DESKTOPs_101_a_119

1. Clique em **Add**
2. **Group Name:** `DESKTOPs_101_a_119`
3. Em **Available Address**, selecione `DESKTOPs_101_a_119` (criado no passo anterior)
4. Clique na seta **→** para mover para **Selected Address**
5. Clique em **OK**

#### Criar Grupo: DESKTOP_120

1. Clique em **Add**
2. **Group Name:** `DESKTOP_120`
3. Em **Available Address**, selecione `DESKTOP_120`
4. Clique na seta **→** para mover para **Selected Address**
5. Clique em **OK**

> **Importante:** Esta etapa é obrigatória. Definir apenas os endereços IP em "IP Address" não cria efetivamente os grupos para uso nas regras de filtragem.

---

## 4. Configuração dos Grupos de Sites (Web Group)

**Menu:** `Behavior Control > Web Filtering > Web Group`

Em **Web Group List** adicione, informando o nome e o grupo de sites que deseja bloquear.

- Nome: 
```
RedesSociais
```
- Sites:
```
youtube.com
m.youtube.com
*.youtube.com
youtu.be
ytimg.com
*.googlevideo.com
facebook.com
*.facebook.com
instagram.com
*.instagram.com
tiktok.com
*.tiktok.com
msn.com
*.msn.com
kwai.com
*.kwai.com
twitter.com
*.twitter.com
```

(Obriga os computadores a utilizarem o serivor DNS forncedo pela empresa de internet)
- Nome: 
```
DoH_Domains
```
- Sites:
```
dns.google
dns.google.com
cloudflare-dns.com
security.cloudflare-dns.com
family.cloudflare-dns.com
quad9.net
dns.quad9.net
nextdns.io
doh.opendns.com
dns.adguard.com
family.adguard-dns.com
unfiltered.adguard-dns.com
doh.cleanbrowsing.org
family-filter-dns.cleanbrowsing.org
adult-filter-dns.cleanbrowsing.org
security-filter-dns.cleanbrowsing.org
doh.securedns.comodo.com
doh.mullvad.net
doh.opennic.org
dnsovertls.sinodun.com
dnsovertls1.sinodun.com
dns.aa.net.uk
doh.powerdns.org
doh.appliedprivacy.net
```

- Outros DoH que podem ser adicionados.
```
*.joindns4.eu
protective.joindns4.eu
child.joindns4.eu
noads.joindns4.eu
child-noads.joindns4.eu
unfiltered.joindns4.eu

*.controld.com
*.controld.io
freedns.controld.com
restricted.controld.com
family.controld.com

# NextDNS
*.nextdns.io
dns.nextdns.io

*.dnsfilter.com
*.dnsfilter.org

*.webtitan.com
*.titanhq.com

*.safedns.com
filter.safedns.com

*.cleanbrowsing.com
dns.cleanbrowsing.com
*.securedns.com
*.securedns.org
*.powerdns.org
doh.dns.apple.com
dns.apple.com
private.dns.apple.com
```

- Nome:
```
Improprios
```
- Sites:
```
*.bongacams.com
*.chaturbate.com
*.adultfriendfinder.com
*.sex.com
*.hclips.com
*.spankbang.com
*.fapster.com
*.bet365.com
*.pokerstars.com
*.888casino.com
*.1xbet.com
*.betfair.com
*.williamhill.com
*.bodog.com
*.leovegas.com
*.partycasino.com
*.casinostars.com
*.sportingbet.com
*.buyweedonline.com
*.weedmaps.com
*.drugstore.com
*.cannabis.net
*.420magazine.com
*.leafly.com
*.guns.com
*.ammoseek.com
*.cheaperthandirt.com
*.gunbroker.com
*.armslist.com
*.darkweb.com
*.torlinks.com
*.proxies.com
*.vpnbypass.com
*.unblocksite.com
*.pornhub.com
*.xvideos.com
*.redtube.com
*.xnxx.com
*.youporn.com
*.onlyfans.com
*.cam4.com
*.livejasmin.com
*.stripchat.com
```

- Nome:
```
Jogos
```
- Sites:
```
poki.com
*.poki.com
poki.com.br
*.poki.com.br
poki.pt
*.poki.pt
poki2.net
*.poki2.net
frivjogosonline.com.br
*.frivjogosonline.com.br
roblox.com
*.roblox.com
vigoo.fun
*.vigoo.fun
clickjogos.com.br
*.clickjogos.com.br
jogos360.com.br
*.jogos360.com.br
ojogos.com.br
*.ojogos.com.br
jogosjogos.com
*.jogosjogos.com
gaamess.com
*.gaamess.com
miminogames.com
*.miminogames.com
friv5online.com
*.friv5online.com
friv2019.com.br
*.friv2019.com.br
friv2019.com
*.friv2019.com
repuls.io
*.repuls.io
minijogos.com.br
*.minijogos.com.br
crazygames.com.br
*.crazygames.com.br
crazygames.com
*.crazygames.com
juegosfriv2019.com
*.juegosfriv2019.com
yurk.com
*.yurk.com
```
---

## 5. Configuração das Regras de Filtragem

**Menu:** `Behavior Control > Web Filtering > Web Group Filtering`

### 5.1. Ativar Filtro Globalmente

Antes de criar as regras, role até a seção **General** no topo da página e:
1. Marque a opção **Enable Web Filtering**
2. Clique em **Save**

### 5.2. Criar Regra para DESKTOPs_101_a_119

1. Clique em **Add**
2. Preencha os campos:

| Campo | Valor |
|-------|-------|
| **IP Group** | DESKTOPs_101_a_119 |
| **Policy** | Block |
| **Web Group** | *(selecione os grupos de sites desejados)* |
| **Effective Time** | Any |
| **Status** | Enable |

3. Clique em **OK**

### 5.3. Criar Regra para DESKTOP_120

1. Clique em **Add**
2. Preencha os campos:

| Campo | Valor |
|-------|-------|
| **IP Group** | DESKTOP_120 |
| **Policy** | Block |
| **Web Group** | *(selecione os grupos de sites desejados)* |
| **Effective Time** | Any |
| **Status** | Enable |

3. Clique em **OK**

### 5.4. (Opcional) Criar Regra para Todos os IPs da LAN

1. Clique em **Add**
2. Preencha os campos:

| Campo | Valor |
|-------|-------|
| **IP Group** | IPGROUP_LAN (grupo padrão que inclui toda a rede LAN) |
| **Policy** | Block |
| **Web Group** | *(selecione grupos de sites para bloqueio geral)* |
| **Effective Time** | Any |
| **Status** | Enable |

3. Clique em **OK**

### 5.5. Verificar Ordem das Regras

Após criar as regras, verifique a lista. As regras são processadas da **menor ID para a maior ID** (prioridade numérica):

- Regras mais específicas (grupos menores) devem ter IDs menores (maior prioridade)
- Regras mais genéricas devem ter IDs maiores (menor prioridade)

Se necessário, exclua e recrie as regras na ordem desejada.

---

## 6. Salvando e Aplicando Configurações

1. Após criar todas as regras, clique em **Save** no final da página
2. Aguarde a confirmação de que as configurações foram aplicadas

---

## 7. Testando o Funcionamento

### 7.1. Teste Imediato
1. Em um computador do grupo `DESKTOPs_101_a_119`, tente acessar um site que deveria estar bloqueado
2. Em um computador do grupo `DESKTOP_120`, tente acessar sites que deveriam estar liberados ou bloqueados conforme configurado

### 7.2. Se o site não for bloqueado
- **Limpe o cache do navegador:**
  - Chrome/Edge: `Ctrl + Shift + Del` > marcar "Imagens e arquivos em cache" > limpar
  - Firefox: `Ctrl + Shift + Del` > marcar "Cache" > limpar
- **Teste no modo anônimo/privado** do navegador
- **Use um navegador diferente** que nunca acessou o site antes

---

## 8. Manutenção Periódica

### 8.1. Atualizar Listas de Sites
- Periodicamente, revise e atualize os grupos de sites
- Sites de jogos e redes sociais frequentemente criam novos domínios

### 8.2. Monitorar Logs
**Menu:** `Status > System Log > Security Log`

Verifique regularmente se os bloqueios estão sendo aplicados conforme esperado

### 8.3. Atualizar Firmware
**Menu:** `System Tools > Firmware Upgrade`

Mantenha o firmware do roteador atualizado para garantir o correto funcionamento dos filtros

---

## 9. Solução de Problemas Comuns

| Problema | Possível Causa | Solução |
|----------|----------------|----------|
| Sites não bloqueados | Web Filtering desativado | Ativar "Enable Web Filtering" na seção General |
| Grupos não aparecem | Grupos não criados em "IP Group" | Criar grupos em Preferences > IP Group > IP Group |
| Regras não funcionam | Ordem incorreta | Verificar IDs das regras (menor ID = maior prioridade) |
| Site bloqueado abre | Cache do navegador | Limpar cache ou testar em modo anônimo |

---

**Data da configuração:** 05/03/2026  
**Equipamento:** TP-Link ER605  
**Versão do firmware:** (verificar atualizações periodicamente)