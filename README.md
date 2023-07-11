<h3> React - Lidando com arquivos estáticos (Alura) </h3>


O Sass é uma variação do CSS, com funcionalidades adicionais, que agiliza a criação de estilos e deve ser compilada para CSS. O Sass oferece algumas ferramentas que facilitam a escrita, como aninhamento. Entretanto, o navegador interpreta apenas CSS e, por isso, o arquivo Sass, que é escrito em desenvolvimento, é compilado para CSS puro.
O typescript-plugin-css-modules oferece tipagem para os estilos e facilita o uso dos estilos como módulos em componentes pois possibilita o uso do autocomplete. A biblioteca consegue entender o módulo CSS como um módulo em TypeScript e, junto aos editores de código como o VSCode, é capaz de oferecer sugestões sobre as propriedades disponíveis.
O Sass é utilizado pelos componentes via CSS Modules. O CSS Modules e o TypeScript usados em componentes são convertidos em JavaScript para a aplicação rodar nos navegadores, e o Sass é convertido para CSS. Todas essas bibliotecas trabalham juntas, fazendo algum tipo de conversão para que o código escrito seja compreendido pelo navegador. Enquanto o Sass facilita a escrita de estilos, o CSS Modules facilita a aplicação desses estilos e o TypeScript ajuda na experiência de desenvolvimento dos componentes.


O npm run start, por debaixo dos panos, ele gera uma pasta build em memória, e ele roda essa pasta “build” no navegador para nós. Então o npm run build, ao invés de gerar em memória, ele gera para nós fisicamente mesmo a pasta “build”.

Se a rota da imagem for passada dentro do img="../../assets/logo.svg" o nosso SVG não foi para a pasta “build”. Por quê? Se voltarmos no nosso “index.tsx” do cardápio, o SRC da imagem é uma String, é uma coisa estática. E o Webpack, que gera esse build, ele não consegue entender que esse path, esse SRC é de um arquivo estático, ele não consegue compreender isso.
E como o Create React App faz para conseguir avisar para o Webpack que esse SVG é um arquivo estático e que ele precisa levar em consideração na hora do build? Para que ele consiga fazer isso, precisamos importa-lo, da mesma forma que importamos o CSS Modules. 
*Solução: omportar a rota =  import logo from ‘../../assets/logo.svg’, assim pega o logo, e ao invés do SRC ser uma string estática, assim no img é só abrir chave e colocar o logo dentro. Agora ele vai gerar a pasta “build” em memória.
Outra forma: quando não quer que o logo venha de uma imagem, queremos que o logo, que o SVG, seja um SVG mesmo. E como conseguimos fazer isso? O Create React App já traz um pacote para nós chamado SVGR, que ele converte um SVG para um componente React. E para conseguirmos utilizar o SVGR, precisamos colocar uma chave no logo, e escrever reactComponent as Logo, isso, ele nos converte um componente React com o meu nome logo desse SVGR.
Na prática, basta tirar o img, e ao invés de ser uma tag img, eu vou colocar uma tag <Logo />, literalmente, como se fosse um componente.

Configuração do tsconfig.json para deixar padrão a rota: dentro de “compiler options”, só colocar uma opção chamada baseUrl, e essa é a URL padrão que vamos querer importar alguma coisa. E queremos que seja padrão de SRC, normalmente não saímos de lá. "baseUrl": "src"
