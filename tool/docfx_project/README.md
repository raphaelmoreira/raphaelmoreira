# Gestão do website
Conteúdo gerado através da ferramenta DocFx.

# Passos
Criando e executando um novo projeto de documentação.
```
dotnet tool install docfx --global
dotnet tool update -g docfx
mkdir tool
cd tool
mkdir docfx_project
cd docfx_project
docfx init
docfx tool/docfx_project/docfx.json --serve
```
- Edite o `toc.yml` na raiz para produzir os menus principais (superiores)
- Efetue o `commit` para o respositório
- No repositório, clique no menu **Settings**
- Na seção **Code and automation**, clique em **Pages**
- Em **Build and deployment**, selecione a fonte **GitHub Actions**
- Na opção que abriu, opte por **Static HTML** e clique em **Configure**
- Atualize `name` e `jobs:deploy:steps:name(Upload artifact):with:path:(./doc/site)` ou o caminho conforme sua estrutura.
- Efetue o `commit` e verifique se está de acordo.