[README.md](https://github.com/user-attachments/files/31558684/README.md)
# Cloud Cost Dashboard

Dashboard para análise de custos de AWS, Azure e OCI. Lê arquivos CSV ou Excel direto no navegador — nenhum dado sai da sua máquina.

## Como publicar no GitHub Pages (5 minutos)

### Passo 1 — Criar repositório no GitHub
1. Acesse [github.com/new](https://github.com/new)
2. Dê um nome: `cloud-dashboard`
3. Deixe **público** (necessário para GitHub Pages gratuito)
4. Clique em **Create repository**

### Passo 2 — Fazer upload do arquivo
1. Na página do repositório, clique em **Add file → Upload files**
2. Arraste o arquivo `index.html`
3. Clique em **Commit changes**

### Passo 3 — Ativar GitHub Pages
1. Vá em **Settings → Pages**
2. Em **Source**, selecione `Deploy from a branch`
3. Branch: `main` / Folder: `/ (root)`
4. Clique em **Save**

Após ~1 minuto, seu dashboard estará em:
```
https://SEU-USUARIO.github.io/cloud-dashboard
```

---

## Formato esperado do CSV/Excel

| Coluna | Obrigatório | Descrição |
|--------|-------------|-----------|
| `service` | ✅ | Nome do serviço (EC2, S3, Virtual Machines...) |
| `cost` | ✅ | Custo em USD |
| `date` | ✅ | Data ou mês (ex: 2025-01-01 ou 2025-01) |
| `cloud` | ✅ | Provedor: aws, azure ou oci |
| `region` | ✅ | Região (us-east-1, brazilsouth...) |
| `instance_id` | ⚡ | ID ou nome do recurso (para drill-down) |
| `instance_type` | ⚡ | Tipo da instância (t3.medium, Standard_D2s...) |
| `cpu_avg` | ⚡ | Utilização média de CPU em % |
| `mem_avg` | ⚡ | Utilização média de memória em % |
| `storage_gb` | ⚡ | Tamanho do disco em GB |

> ⚡ = opcional, mas necessário para análise de recursos e recomendações

O dashboard aceita variações nos nomes das colunas em português e inglês.

---

## Como exportar dados de cada cloud

### AWS — Cost & Usage Report (CUR)
1. AWS Console → Billing → Cost & Usage Reports
2. Crie um relatório com granularidade **Monthly**
3. Inclua **Resource IDs**
4. Para métricas de CPU: CloudWatch → Export → EC2 `CPUUtilization`

### Azure — Cost Management
1. Portal Azure → Cost Management + Billing → Cost Analysis
2. Clique em **Download** → selecione CSV
3. Para métricas de VM: Monitor → Metrics → Export

### OCI — Cost and Usage Reports
1. OCI Console → Governance → Cost Management → Cost and Usage Reports
2. Faça download do CSV mensal
3. Para métricas: Monitoring → Metrics Explorer → Export

---

## Recursos do dashboard

- **Visão geral**: gráficos de serviços, clouds, evolução temporal e regiões
- **Recursos**: drill-down por serviço com lista de instâncias, CPU, memória e status
- **Recomendações**: engine automático que identifica instâncias ociosas, superdimensionadas e oportunidades de Reserved Instances
- **Detalhes**: tabela completa com todos os registros
- Filtros por cloud e período
- Dark mode automático
- 100% client-side — nenhum dado sai do navegador
