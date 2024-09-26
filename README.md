# Questão 2: API de Receitas

## Descrição do Projeto

Neste projeto, implementamos um **componente React** que consome uma API de receitas, especificamente a **API do Recipe Puppy**. O objetivo é exibir uma lista de receitas, mostrando o nome e a imagem de cada uma.

## Objetivos

- **Consumir uma API** para obter receitas de forma dinâmica.
- **Exibir uma lista** de receitas com informações visuais, incluindo nome e imagem.
- Oferecer uma experiência de usuário interativa e intuitiva.

## Detalhes Técnicos

O componente utiliza o hook `useEffect` para buscar as receitas assim que o componente é montado. Abaixo está uma estrutura básica do código:

```javascript
import React, { useState, useEffect } from 'react';

const App = () => {
  const [recipes, setRecipes] = useState([]);

  const fetchRecipes = async () => {
    try {
      const response = await fetch('https://api.recipepuppy.com/api/');
      const data = await response.json();
      setRecipes(data.results);
    } catch (error) {
      console.error('Erro ao buscar receitas:', error);
    }
  };

  useEffect(() => {
    fetchRecipes();
  }, []);

  return (
    <div>
      <h1>Lista de Receitas</h1>
      <ul>
        {recipes.map((recipe) => (
          <li key={recipe.title}>
            <h2>{recipe.title}</h2>
            <img src={recipe.image} alt={recipe.title} />
          </li>
        ))}
      </ul>
    </div>
  );
};

export default App;
