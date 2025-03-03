# Gestão do website
O conteúdo do site é gerado através da ferramenta DocFx (v2.78.3). Caso deseje propor novos conteúdos ou corrigir o que
existe, valide suas alterações antes, publicando localmente a página, antes de enviar ao repositório. Para isso, siga os
passos abaixo.

Instale a última versão da ferramenta através do comando (se já existir, ele aplica a atualização automaticamente):

```
dotnet tool install docfx --global
```
Caso tenha certeza de que a ferramenta existe, utilize apenas:
```
dotnet tool update -g docfx
```
Através do Terminal/PowerShell, navegue até o diretório raiz e faça:
```
mkdir tool
cd tool
mkdir docfx_project
cd docfx_project
docfx init
```
Esse processo vai lhe direcionar nas etapas de criação de um novo site. Ele irá requisitas as informações:

| Parâmetro                        | Descrição                                                      | Valor           |
|----------------------------------|----------------------------------------------------------------|-----------------|
| Name (mysite)                    | É o nome que você quer para seu site.                          | Meu Site        |
| Generate .NET API documentation? | Caso você tenha código C#, este também será integrado ao site. | n               |
| Markdown docs location (docs)    | Caminho onde consta a documentação em markdown (md).           | minha-categoria |
| Enable site search?              | Adiciona um campo de busca em seu site.                        | y               |
| Enable PDF?                      | Permite exportar o conteúdo das páginas em PDF                 | y               |

Isso vai lhe gerar os arquivos `toc.yml`, `docfx.json` e `index.md` na raiz da pasta `docfx_project`. Confirme.

# Ajustes
As etapas a seguir visam refinar a configuração:

## Edite o arquivo `docfx.json` e modifique o seguintes trechos:
- Localize a chave `build:content:exclude` e substitua `"_site/**"` por `"../../doc/site/**"`;
- Localize a chave `build:output` e substitua `"../../doc/site"` por `"../../doc/site"`;
- Localize a chave `build:globalMetadata` e acrescente o atributo `"_appLogoPath": ""`.

# Testando
Para validar o funcionamento em `localhost`, execute o comando na raiz do repositório:

```
docfx tool/docfx_project/docfx.json --serve
```

_Obs: em sua última versão, a execução depende do Chrome Headless Shell (playwright)._

# Publicando
- O arquivo `toc.yml` é usado para produzir os menus principais (superiores);
- Efetue o `commit` para o repositório;
- No repositório, clique no menu **Settings**
- Na seção **Code and automation**, clique em **Pages**
- Em **Build and deployment**, selecione a fonte **GitHub Actions**
- Na opção que abriu, opte por **Static HTML** e clique em **Configure**
- Atualize `name` e `jobs:deploy:steps:name(Upload artifact):with:path:(./doc/site)` ou o caminho conforme sua estrutura.
- Efetue o `commit` e verifique se está de acordo.
