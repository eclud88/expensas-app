# As Minhas Despesas — PWA offline v1.1

Aplicação pessoal de registo de despesas, com interface em português europeu, armazenamento local IndexedDB e cache offline.

## Funcionalidades desta versão
- Registo de despesas com data, categoria, subcategoria, estabelecimento e notas.
- Cada despesa contém um ou mais artigos, sempre com nome, quantidade e preço unitário.
- Subtotais por artigo e total automático da compra.
- Resumo mensal e anual, totais por categoria e artigos com maior valor acumulado.
- Histórico pesquisável e filtrável por datas e categoria.
- Adição de subcategorias personalizadas.
- Exportação/importação manual de cópia de segurança JSON.
- Eliminação individual e limpeza completa com confirmação.
- Registo automático do Service Worker e cache offline dos ficheiros essenciais.

## Limitações conhecidas da v1
- Os totais por artigo são agregados pelo nome do artigo; diferenças de marca ou tamanho devem ser registadas no nome se for necessário distingui-las.
- Os totais de categoria/subcategoria são calculados com base nos registos guardados; a subcategoria escolhida descreve a despesa e os artigos ficam associados a ela.
- Não há sincronização, contas, OCR de talões, orçamento, despesas recorrentes nem exportação CSV nesta primeira versão.
- Os dados não são enviados para um servidor. Limpar os dados do Safari ou perder o dispositivo pode eliminar os registos; exporta backups regularmente.
- A cache offline é ativada após a primeira abertura com ligação e instalação/carregamento dos recursos.

## Instalação no iPhone
Uma PWA instalável requer publicação num alojamento HTTPS. O ficheiro ZIP, por si só, não instala a aplicação no iPhone.

1. Descompacta a pasta.
2. Publica o conteúdo da pasta num alojamento HTTPS estático (por exemplo, GitHub Pages ou outro alojamento estático compatível).
3. Abre o endereço HTTPS no Safari do iPhone e espera que a página carregue totalmente com Internet.
4. Toca em Partilhar → Adicionar ao ecrã principal.
5. Abre a aplicação a partir do novo ícone e testa o registo.
6. Com a aplicação carregada, ativa o modo de voo e confirma que consegues navegar, criar uma despesa e consultar o histórico.
7. Vai a Dados → Exportar cópia de segurança e guarda regularmente o ficheiro num local seguro.

## Testar localmente no computador
Não abras simplesmente `index.html` com duplo clique se quiseres testar a funcionalidade offline do service worker: este requer HTTPS ou localhost.

Com Python instalado, a partir desta pasta:
```bash
python3 -m http.server 8000
```
Depois abre `http://localhost:8000`. Isto serve para testar no computador; não torna o endereço acessível ao iPhone nem fornece HTTPS para instalação PWA.

## Segurança e privacidade
Os dados de despesas ficam no armazenamento local do navegador. A exportação gera um ficheiro JSON sem encriptação; protege o ficheiro se contiver informação privada. Esta versão não substitui uma cópia de segurança externa.
