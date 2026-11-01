# BloxTracker updates

Canal oficial de atualização do BloxTracker. Versão atual: **3.3.0**.

## Atualizar

No PC central, abra **Atualizações**, salve a fonte abaixo e use **Verificar versão → Baixar atualização → Instalar e reiniciar**.

```
https://raw.githubusercontent.com/danielsolzapo-dev/BloxTracker-updates/main/manifest.json
```

Depois selecione os agentes de destino e solicite a atualização pela rede. O atualizador precisa estar instalado uma vez em cada computador. Configurações, contas, banco de dados e chaves ficam nos PCs e não fazem parte do pacote público.

## Versão 3.3.0

- Visual neon com três cores de destaque.
- Visão por PC com contas, metas e consumo dos processos vinculados.
- Estados inferidos das contas; dados recentes não confirmam execução de farm.
- Perfis persistentes de RAM e CPU para as contas selecionadas.
- Versão por PC, notas de atualização e seleção dos agentes.

CPU observada é percentual do total do PC. RAM observada é o working set em MiB. Cobertura informa quantos PIDs foram medidos; agentes antigos precisam atualizar para fornecer consumo.

## Arquivos

`manifest.json` e `package.zip` são publicados juntos. SHA-256 verifica integridade; confie somente em fontes administradas por você. O pacote contém código executável. O tracker mantém backup da aplicação para recuperação.
