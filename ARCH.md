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

## Decisões
- Validação mínima ficou no `TodoViewModel` (título não vazio).
- Parsing JSON ficou no `TodoModel` (camada data).
- Erros são propagados como `Exception` e traduzidos em mensagem no ViewModel.
