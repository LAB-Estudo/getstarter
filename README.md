# MQLab ReactJS metodologia de desenvolvimento

## Bibliotecas utilizadas

Escrevendo...

## Overview

Escrevendo...

## Componentes de interface

Escrevendo...

Eles são construídos em duas frentes. 

### Frente nº 1

A primeira frente é focada em construi-los da maneira mais simples possível permitindo que eles sejam extremamente reaproveitados.

Alguns exemplos:

- `<EX.DatePicker />`
- `<LT.Content />`
- `<UI.Input />`

Todos esses componentes são divididos em três principais grupos `EX`, `LT` e `UI`.

Esses componentes são construídos em um projeto separado e utilizado como se fosse um framework de interface (como o Bootstrap ou o Bulma) para garantir que os componentes sempre sejam o mais simples e reutilizável possível.

#### `EX` Extend 

Componente que estendem outros componente em especial componentes Open Source.

Geralmente são construídos apenas criado um novo estilo ou uma pequena modificação de comportamento para que sempre que ocorra uma mudança na interface ou nas regras de negocio essa alteração seja feita em toda a aplicação.

Alguns exemplos:

- `<EX.Modal />`
- `<EX.Autoseggest />`

#### `LT` Layout 

Componente que não possuem nenhum tipo de interação e tem como objetivo simplesmente delimitar areas da interface, como cabeçalho, rodapé, menu, timeline e etc.

Alguns exemplos:

- `<LT.Header />`
- `<LT.Sidebar />`

#### `UI` User Interface

Componente que irão ser reutilizados para construir a interface e devem ser o mais simples possível para que possam ser reaproveitados e estendidos por outros componentes mais complexos.

Alguns exemplos:

- `<UI.Button />`
- `<UI.Tag />`

### Frente nº 2

A segunda frente já tem como objetivo compor a interface. Criando novos componente utilizando todos os componente criados na etapa anterior.

Alguns exemplos.

- `<FormTransaction />`
- `<Login />`
- `<Timeline />`

### Stateless

Escrevendo...

Todos os componentes relacionado a interface deverão ser stateless. Ou seja, componente que não possuem estado interno e dependem das props ou de um gerenciador de estado como Redux ou MobX para controlar o que deve ser exibido.

Para construir um componente stateless, devemos utilizar funções  (React Functional Stateless Component) para construir nossos componentes:

```javascript
const Button = (props) => (
	const { children, ...rest } = props;
	
  return <button {...rest}>{ children }</div>; 
)
```

Quais as vantagens de se utilizar componentes stateless:

- Como o componente não possui estado interno ele deve consumir isso do nosso gerenciador de estado. Permitindo que toda a aplicação posso consumir o mesmo dado e sempre que ele for alterado os componente que dependem dele serão atualizado automaticamente.
- São mais fáceis de serem compreendidos se comparados com classes do ES2015+.

### Props

Escrevendo...

#### propTypes

A declaração das PropTypes é de extrema importância pois elas iram nos ajudar em diversos momentos:

- Servirão de documentação para o componente. Sempre alguém precisar utilizar o componente poderemos prever qual props e seu tipo cada componente está esperando receber.
- Irão garantir que estamos passando os dados corretamente, tornando mais fácil o diagnóstico de problemas.
- Seremos alertados quando um prop está recebendo um tipo diferente.
- Seremos capazes de utilizar o react-docgen para gerar um documentação oficial dos nossos componente.

```javascript
import React, { PropTypes } from 'react';

const SearchInput = (props) => (
	const {
		// states
	  text,
	  resultsCount,
	  hovered,
	
	  // callbacks
	  onChangeText,
	  onClickCancel,
	  onHover,
	} = props;
  ...
);

SearchInput.propTypes = {
		// states
    text: PropTypes.string.isRequired,
    resultsCount: PropTypes.number,
    hovered: PropTypes.bool.isRequired,

	  // callbacks
    onChangeText: PropTypes.func.isRequired,
    onClickCancel: PropTypes.func.isRequired,
    onHover: PropTypes.func.isRequired
};
```

*OBS: Durante a declaração das propTypes: Primeiro propriedades de estado do componente e depois callbacks (funções) sempre mente-las em ordem alfabética.*

#### defaultProps

Escrevendo...

## Storybook

Escrevendo...

## Routes e Pages

Escrevendo...

## Actions e Reducers

Escrevendo...

## Testes

Escrevendo...

## Containers

Escrevendo...

## Extras

Escrevendo...

Aqui temos algumas ferramentas que utilizamos no dia a dia para desenvolver.

### Produtividade

Escrevendo...

### Deploy

Escrevendo...

### Plugins que recomendamos

#### Plugins para o Visual Studio Code

- [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome#review-details)
- [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig#review-details)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint#review-details)
- [language-stylus](https://marketplace.visualstudio.com/items?itemName=sysoev.language-stylus#review-details)
- [Node.js Extension Pack](https://marketplace.visualstudio.com/items?itemName=waderyan.nodejs-extension-pack#review-details)
- [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync#review-details)
- [Sort JSON objects](https://marketplace.visualstudio.com/items?itemName=richie5um2.vscode-sort-json#review-details)
- [Stylint](https://marketplace.visualstudio.com/items?itemName=vtfn.stylint#review-details)
- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint#review-details)

#### Plugins para o Chrome

Deve ser revisado...

- [Apollo Client Developer Tools](https://chrome.google.com/webstore/detail/apollo-client-developer-t/jdkknkkbebbapilgoeccciglkfbmbnfm) **
- [React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)
- [React Perf](https://chrome.google.com/webstore/detail/react-perf/hacmcodfllhbnekmghgdlplbdnahmhmm) **
- [Redux Devtools](https://github.com/zalmoxisus/redux-devtools-extension)
- [Wappalyzer](https://wappalyzer.com/) **
- [What Font?](http://www.chengyinliu.com/whatfont.html)
- [ColorZilla](https://chrome.google.com/webstore/detail/colorzilla/bhlhnicpbhignbdhedgjhgdocnmhomnp)
- [CSSViewer](https://chrome.google.com/webstore/detail/cssviewer/ggfgijbpiheegefliciemofobhmofgce)
- [CodeCopy](https://chrome.google.com/webstore/detail/codecopy/fkbfebkcoelajmhanocgppanfoojcdmg)

## Referência 
Nós utilizamos alguns outros guias para a construção da nossa metodologia. 

Para saber mais sobre nossas referências:

- [Rafael Ribeiro](https://github.com/rafaelcorreiapoli/react-metodologia/blob/master/README.md)