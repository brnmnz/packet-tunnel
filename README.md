# StopBet VPN — Monitoramento de Domínios via Packet Tunnel

StopBetVPN é uma extensão de rede para iOS desenvolvida com `NEPacketTunnelProvider`, com o objetivo de monitorar domínios acessados pelo usuário em tempo real.  
Esse projeto faz parte da iniciativa **StopBet**, focada em ferramentas para bloquear ou alertar sobre o uso de sites de apostas.

---

## 🚀 Funcionalidades

- 🔒 Criação de túnel de rede personalizado via `NetworkExtension`
- 🧠 Análise de pacotes DNS para identificar domínios acessados
- 📡 Leitura contínua de tráfego DNS com `packetFlow`
- ✅ Estrutura pronta para expansão: bloqueio, logs, alertas, etc.

---

## 🧩 Estrutura

```
StopBetVPN/
├── PacketTunnelProvider.swift     # Extensão VPN baseada em NEPacketTunnelProvider
├── DNSMonitorService.swift        # Serviço de extração de domínio via leitura bruta de pacotes
├── Info.plist                     # Configurações da extensão
├── StopBetVPN.entitlements        # Permissões específicas para Network Extensions
```

## 🛠 Pré-requisitos
Para testar e distribuir este projeto, é necessário:

- Conta ativa no Apple Developer Program
- Dispositivo físico (iPhone/iPad) — não funciona em simulador

🧾 App ID com capability ativada:
Network Extensions → Packet Tunnel Provider

⚙️ Configuração correta dos provisioning profiles e .entitlements

## ⚙️ Como funciona
Ao iniciar o túnel, o sistema redireciona o tráfego para a extensão.

A função packetFlow.readPackets lê os pacotes DNS.

O DNSMonitorService interpreta os bytes e extrai o domínio acessado.

O domínio é impresso no console e pode ser tratado (log, bloqueio, etc).

🧪 Exemplo de saída no console
```Usuário acessou: bet365.com.
Usuário acessou: youtube.com.
Usuário acessou: blaze.com.```
