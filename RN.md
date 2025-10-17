# 🏭 Regras de Negócio — Sistema SCADA

Documento que define as **diretrizes funcionais, operacionais e de segurança** do sistema SCADA.

---

## 🔐 Controle de Acesso e Segurança

> Regras relacionadas à autenticação, permissões e integridade do sistema.

**RN01** — Todo usuário deve possuir um nível de acesso associado: **Operador**, **Técnico**, **Supervisor** ou **Administrador**.  
**RN02** — Operadores só podem executar comandos de controle (ligar/desligar) se possuírem permissões adequadas.  
**RN03** — Técnicos e administradores podem aplicar fatores de correção e reconfigurar parâmetros de controle.  
**RN04** — O sistema deve bloquear tentativas de login após **5 falhas consecutivas**, liberando somente após **autenticação administrativa** ou após **15 minutos**.  
**RN15** — Todos os logs de eventos e operações devem ser armazenados de forma **imutável**, com **assinatura digital**.  
**RN16** — Logs devem ser **retidos por, no mínimo, 5 anos**.  
**RN17** — Alterações em alarmes, limites de processo e calibrações devem gerar **auditoria automática**.  
**RN20** — O sistema deve **validar pacotes de dados recebidos** para garantir integridade e evitar comandos não autorizados.  

---

## ⚙️ Operação e Comandos

> Regras que definem a execução e o controle de processos.

**RN06** — Comandos de controle só podem ser executados sobre equipamentos com status **“disponível”** e **comunicação ativa com o CLP**.  
**RN07** — Todo comando enviado ao CLP deve exigir **confirmação de recebimento (ACK)** antes de atualizar o status na HMI.  
**RN08** — Caso o CLP não responda em até **3 segundos**, o comando é considerado **falho** e registrado como erro no log.  
**RN09** — O sistema deve impedir o envio simultâneo de **comandos conflitantes** (ex: ligar e desligar).  
**RN10** — Parâmetros de controle alterados via HMI só entram em vigor após **validação do técnico responsável** e **registro em log**.  
**RN26** — Comandos críticos devem ter **tempo máximo de resposta de 1 segundo** entre envio e confirmação.  

---

## 🚨 Alarmes e Eventos

> Políticas de detecção, classificação e resposta a condições anormais.

**RN11** — Alarmes devem ser classificados por criticidade:  
🟢 Baixa 🟡 Média 🔴 Alta 🚨 Emergência  

**RN12** — Alarmes de **Alta** e **Emergência** devem gerar **notificação sonora e visual imediata** e permanecer ativos até **reconhecimento manual**.  
**RN13** — Alarmes reconhecidos **não podem ser apagados** do histórico.  
**RN14** — Caso uma variável ultrapasse o limite crítico, o sistema deve:  
- Registrar o evento automaticamente  
- Emitir alarme correspondente  
- Sugerir ações corretivas configuradas  

---

## 🧾 Registro e Auditoria

> Regras sobre rastreabilidade, logs e relatórios do sistema.

**RN05** — Todas as ações executadas por um usuário devem ser **registradas em log** com **data, hora, ID do usuário e equipamento afetado**.  
**RN18** — Relatórios devem conter **identificação do emissor**, **data** e **filtros aplicados**.  
**RN23** — Toda **manutenção** deve ser registrada com **data, técnico, tipo de intervenção** e **equipamentos envolvidos**.  
**RN24** — Fatores de correção aplicados a sensores devem ser **documentados e revertíveis**.  
**RN25** — O histórico de manutenção deve ser **filtrável por equipamento, data e tipo de intervenção**.  

---

## 🌐 Comunicação e Redundância

> Regras que asseguram conectividade, confiabilidade e disponibilidade contínua.

**RN19** — Comunicação com CLPs deve seguir protocolos industriais padronizados:  
`Modbus TCP`, `OPC UA`, `IEC 60870`.  
**RN21** — Em caso de falha de comunicação, o sistema tenta **reconexão automática a cada 5 segundos**, sem limite de tentativas.  
**RN22** — Se o servidor principal falhar, o **servidor redundante** deve assumir **automaticamente em até 30 segundos**, **sem perda de dados**.  
**RN27** — A perda de comunicação com um servidor **não deve interromper a supervisão** dos processos.  

---

## 💾 Backup e Confiabilidade

> Políticas de persistência e disponibilidade dos dados.

**RN28** — O sistema deve realizar **backup completo automaticamente a cada 24h**, mantendo **os 7 últimos backups**.  
**RN29** — Atualizações de software devem ser **aplicáveis sem parar a operação (hot update)**.  
**RN30** — O sistema deve operar continuamente por **no mínimo 6 meses sem falhas críticas**.  

---

## 🖥️ Interface e Visualização

> Diretrizes visuais e funcionais da interface do sistema.

**RN31** — Gráficos em tempo real devem ser **atualizados automaticamente** (sem atualização manual).  
**RN32** — A interface deve conter **equipamentos e seus status**, com **informações ao vivo**.  
**RN33** — Elementos de interface (ícones, alarmes, botões) devem seguir um **padrão visual de cores e estados**, conforme definido no **Manual de Operação**.  

---

## 📚 Autor

**Projeto:** MattSchutz SCADA System
**Versão:** 2.2  
**Data:** _(17/10/2025)_

---
