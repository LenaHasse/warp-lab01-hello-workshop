##Uruchomienie

commit23

commit3

## Kontakt

Autor: Student - Warsztat Programisty



##Wymagania

commit2

dotnet run

## Continuous Integration

W repozytorium jest podpięty prosty pipeline w GitHub Actions (`.github/workflows/build.yml`), który sam sprawdza i buduje projekt.

### Kiedy?
- Przy każdym `push` i `pull_request` do gałęzi `main`.
- Ręcznie z zakładki **Actions** na GitHubie (`workflow_dispatch`).

### Co robi ten workflow?
1. Uruchamia skrypt `scripts/check-repository.sh`, żeby upewnić się, że plik projektu `./HelloWorkshop.csproj` istnieje, a `README.md` nie jest pusty.
2. Instaluje .NET 10.0, pobiera pakiety (`dotnet restore`), kompiluje projekt (`dotnet build`) i go uruchamia (`dotnet run`).
3. Publikuje gotową aplikację (`dotnet publish` do `./artifacts/app`) i wrzuca ją jako paczkę `app-<sha>` do pobrania w podsumowaniu runa (na 7 dni).

### Jak przetestować to lokalnie?
W terminalu Bash (np. WSL/Ubuntu) w głównym folderze repozytorium wystarczy:
```bash
bash scripts/check-repository.sh "./HelloWorkshop.csproj"