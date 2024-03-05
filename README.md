# Cook

<h4 align="center"><a href="https://www.figma.com/file/OtmiLN5WSd1SFfGxwk3tvG/Cook-App?type=design&node-id=0-1&mode=design&t=XwY1q8r5qJPVz7AB-0">Figma</a></h4>

Aplicação que sugere receitas conforme os ingredientes selecionados usando React Native, Expo, Expo router, Supabase e React Native reanimated.

<table align="center">
  <tr>
    <td valign="top"> <img src="https://github.com/aureasiqueira1/cook-app/assets/89463362/d3602bcd-8cde-4394-a219-96822f202bac" width="274.6px" /> </td>
    <td valign="top"><img src="https://github.com/aureasiqueira1/cook-app/assets/89463362/35ef8a3e-6261-4938-af20-627d38fd2689" width="274.6px"/></td>
    <td valign="top"><img src="https://github.com/aureasiqueira1/cook-app/assets/89463362/305e3272-1b5f-494a-95fe-78d7ed38bf36" width="274.6px"/></td>
  </tr>
</table>


## 🎯 Tecnologias utilizadas

- React Native
- Expo
- Expo router
- Supabase
- React Native reanimated  

## 🪓 Funcionalidades

- Escolher ingredientes
- Limpar ingredientes
- Buscar receitas
- Ver receitas

## ⚙️ Como executar

Clone o projeto em sua máquina
```bash
  git@github.com:aureasiqueira1/cook-app.git
```

Abra o projeto
```bash
  cd cook-app
```

Instale as dependencias (com yarn ou npm)
```bash
  npm install
```

Inicie o projeto (com yarn ou npm)
```bash
  npx expo start
```


## ⚙️ Obs: Configuração do Supabase

### Crie um novo projeto:
- Login: https://supabase.com/
- New project
- name: cookapp
- Criar senha
- Create new project

 <br />
 
 ### Crie uma nova tabela:
- Table Editor
- Create a new table
- Desabilitar RSL

 <br />
 
  ### Tabela Ingredients:
- name: ingredients
- columns:
  - id uuid ramdom
  - name varchar
  - image text
- Insert
- Insert data from CSV
- Pasta src/database/ingredients_rows

 <br />

 ### Tabela Recipes:
- name: recipes
- columns:
  - id uuid ramdom
  - name varchar
  - minutes int8
  - image text
- Insert
- Insert data from CSV
- Pasta src/database/recipes_rows
  
 <br />
 
 ### Tabela Preparations:
- name: preparations
- columns:
  - id uuid ramdom
  - recipe_id uuid ramdom
  - description text
  - step int8
- Insert
- Insert data from CSV
- Pasta src/database/preparations_rows

   <br />
 
 ### Tabela De Relacionamento entre Receitas e Ingredientes:
- name: recipes_ingredients
- columns:
  - id uuid ramdom
  - recipe_id uuid
  - ingredient_id uuid
- Insert
- Insert data from CSV
- Pasta src/database/recipes_ingredients_rows

 <br />

 ## Imagens:
- Storage
- New bucket
- name: ingredients
- Arrasta imagem da pasta images

 <br />

## Variáveis de ambiente (.env):
- Configurações do projeto
- API
- EXPO_PUBLIC_SUPABASE_URL= URL
- EXPO_PUBLIC_SUPABASE_ANON_KE = anonpublic

 <br />
 
## Adicionar função - SQL Editor:

```sh
CREATE OR REPLACE FUNCTION recipes_by_ingredients(ids UUID[])
RETURNS setof recipes
AS $$
BEGIN
    RETURN QUERY
    SELECT
        recipes.id,
        recipes.name,
        recipes.minutes,
        recipes.image
    FROM
        recipes_ingredients
    INNER JOIN
        recipes ON recipes_ingredients.recipe_id = recipes.id
    WHERE
        recipes_ingredients.ingredient_id = ANY(ids)
    GROUP BY recipes.id;
END;
$$ LANGUAGE plpgsql;
```

## Image Path:
- Supabase - Storage
- Clica em uma imagem
- Get URL
- Remove o último nome da URL
- Substitui imagePath na pasta services/index
  


