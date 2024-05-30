# Gestão do site
Site gerado através da ferramenta DocFx.

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