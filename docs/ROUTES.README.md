## Rotas Aninhadas

As **rotas aninhadas** permitem que você crie uma estrutura de rotas hierárquica. Isso é útil para renderizar componentes que dependem do contexto de rotas pai.

### Como Funcionam

- **Rotas Pai**: Definem o layout ou contexto compartilhado.
- **Rotas Filhas**: Herdam e podem estender o contexto das rotas pai.


## Compartilhamento de Layout

O **compartilhamento de layout** facilita a reutilização de componentes de layout entre diferentes rotas.

### Benefícios

- **Reutilização de Código**: Evita duplicação.
- **Consistência Visual**: Mantém o mesmo layout em diferentes páginas.
- **Manutenção Simplificada**: Alterações no layout são refletidas em todas as rotas que o utilizam.

### Implementação

Utilize o componente `<Outlet />` para renderizar as rotas filhas dentro do layout pai.

Exemplo:

```tsx
// app/routes/dashboard.tsx
export default function DashboardLayout() {
  return (
    <div>
      <Sidebar />
      <main>
        <Outlet />
      </main>
    </div>
  );
}
```


## Rotas Sem Caminho (Pathless Routes)

As **rotas sem caminho** ou **pathless routes** são rotas que não possuem um segmento de URL próprio, mas servem para agrupar rotas e compartilhar lógica ou layouts.

### Quando Usar

- **Agrupamento Lógico**: Quando rotas compartilham o mesmo layout ou lógica.
- **Organização**: Para manter a estrutura de arquivos limpa.

### Como Implementar

Nomeie a pasta da rota com parênteses.

app 
└── routes 
    └── (auth) 
        ├── login.tsx 
        └── register.tsx


- As rotas `login` e `register` compartilharão o mesmo layout definido em `(auth)`.

Exemplo:

```tsx
// app/routes/(auth).tsx
export default function AuthLayout() {
  return (
    <div>
      <Header />
      <Outlet />
      <Footer />
    </div>
  );
}
```

### Utilizando Rotas Sem Caminho para Autenticação
 
app
└── routes
    ├── (admin)
    │   ├── dashboard.tsx
    │   └── settings.tsx
    └── login.tsx

- Rotas dentro de (admin) exigem autenticação.
- login.tsx é acessível publicamente.

![alt text](image.png)