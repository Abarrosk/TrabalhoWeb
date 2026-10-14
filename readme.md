Commit cc706cd:

1. Remoção de Código não usado

Removi contact-phone, contact-email, display-7, navbar-light, parceiros-grid, a classe text (em maintenance.html) e o name="q" das cinco páginas.
Mantive as três variáveis CSS que criámos e não usámos. Todos os selectores de CSS e todos os id estão a ser usados.
Mantive os name e required do formulário de contactos. Como Enviar já não envia nada, deixaram de ter efeito.

2. Responsividade

contactos.html não tinha o JavaScript do Bootstrap, por isso o menu hambúrguer não abria no telemóvel. Já tem.

3. Links - Todos os links são agora iguais para todas as paginas

A navbar e o footer são iguais nas cinco páginas.
A pesquisa da navbar e o botão Enviar não fazem nada. Sem envio, a validação dos campos obrigatórios também deixa de disparar.
“Ver detalhes do curso” em index.html vai para cursos.html, e em cursos.html vai para maintenance.html.
Os links dos cards de contactos continuam com href="#", exceto o telefone de Viseu.

4. Caminhos

Passaram todos a relativos, para funcionarem em qualquer sítio onde a pasta esteja. As quatro páginas dentro de pages/ usam ../ em tudo (por exemplo ../pages/cursos.html, ../images/...).
index.html usa o mesmo sem o ../ (pages/cursos.html, images/...). Não podem ser literalmente iguais, porque index.html está na raiz e as outras numa subpasta.

5. Metas

O head é o mesmo em todas as páginas: charset, viewport, title, description e as etiquetas og: (type, locale, site_name, title, description).
Os títulos são “Pagina Web - Homepage”, “Cursos”, “Parceiros”, “Em Manutencao” e “Contactos”, escritos sem acentos. As descriptions são específicas de cada página.
O lang passou a pt-PT em todas.

6. Favicon e Bootstrap

O favicon está em todas as páginas.
O CSS e o JS do Bootstrap 5.3.8 e o Bootstrap Icons 1.11.3 estão iguais em todas, com o mesmo integrity que já tinhamos

7. Comentários

Retirei todos os comentários de HTML e CSS e não pus nenhum novo.

8. CSS

Os cinco ficheiros ficaram num só, css/styles.css, e todas as páginas chamam apenas esse.
Não havia grandes conflitos. O do footer já era .footer-cesae h5 e o dos cards é .card-title, e mantive esses scopes.
Juntei o que estava duplicado: o :root, o body, as três regras de introdução (agora num selector agrupado), o efeito hover dos cards e o hover dos links dos cards.
O body usa font-family: "Inter", mas essa fonte não é carregada em nenhuma página. Só se vê se estiver instalada no computador. Não mexi.
