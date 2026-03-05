# ARCH — Preencha após refatoração

## Estrutura final (cole a árvore de pastas)
```
lib/
  app/
    app_root.dart
  core/
    errors/
      app_error.dart
  features/
    todos/
      data/
        datasources/
          todo_local_datasource.dart
          todo_remote_datasource.dart
        models/
          todo_model.dart
        repositories/
          todo_repository_impl.dart
      domain/
        entities/
          todo.dart
        repositories/
          todo_repository.dart
      presentation/
        pages/
          todos_page.dart
        viewmodels/
          todo_viewmodel.dart
        widgets/
          add_todo_dialog.dart
  main.dart
```

## Fluxo de dependências
UI -> ViewModel -> Repository -> (RemoteDataSource, LocalDataSource)

## Justificativa da estrutura
- Separei por feature para facilitar a manutenção: tudo de `todos` fica no mesmo lugar, sem caça ao arquivo.
- Mantive a UI simples e focada em renderizar e reagir ao estado, sem conhecer detalhes de rede ou storage.
- Deixei o domínio enxuto, com `Todo` e o contrato do repositório, para servir como base estável caso a implementação mude.
- Coloquei `data` isolada para lidar com HTTP/SharedPreferences e parsing, mantendo essas preocupações longe da tela.

## Decisões
- Validação mínima ficou no `TodoViewModel` (título não vazio) para a UI não precisar repetir regras.
- Parsing JSON ficou no `TodoModel` (camada data), que já conhece o formato da API.
- Erros são propagados como `Exception` e convertidos em mensagem no ViewModel para a tela só exibir o que o usuário precisa.
