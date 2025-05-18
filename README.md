# Guía de Git y GitHub – Prácticas esenciales

Este documento reúce las prácticas más comunes y modernas para trabajar con **Git y GitHub**, incluyendo configuraciones, comandos actualizados y flujos de trabajo profesionales. Ideal para comenzar a trabajar con control de versiones en proyectos colaborativos o personales.

---

## 🔧 Configuración Inicial

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "correo@ejemplo.com"
```

## 🔍 Comandos básicos de Git

| Acción                         | Comando Moderno                    | Descripción                             |
| ------------------------------ | ---------------------------------- | --------------------------------------- |
| Inicializar repositorio        | `git init`                         | Crea un repositorio local.              |
| Ver estado del repo            | `git status`                       | Muestra el estado de los archivos.      |
| Agregar archivos al staging    | `git add archivo.txt`              | Prepara el archivo para commit.         |
| Agregar todos los archivos     | `git add .`                        | Prepara todos los archivos para commit. |
| Crear un commit                | `git commit -m "mensaje"`          | Guarda los cambios localmente.          |
| Ver historial de commits       | `git log`                          | Historial detallado de commits.         |
| Ver historial resumido         | `git log --oneline`                | Historial en una sola línea.            |
| Deshacer staging de un archivo | `git restore --staged archivo.txt` | Saca un archivo del staging.            |
| Revertir cambios en archivo    | `git restore archivo.txt`          | Revierte el archivo al último commit.   |

---

## 📂 Conexión con GitHub

### Crear y subir repositorio:

1. Crear repositorio en GitHub
2. Enlazar el repositorio local:

```bash
git remote add origin https://github.com/usuario/repositorio.git
```

3. Subir por primera vez:

```bash
git push -u origin main
```

### Subir cambios:

```bash
git add .
git commit -m "mensaje descriptivo"
git push
```

### Clonar un repositorio:

```bash
git clone https://github.com/usuario/repositorio.git
```

---

## 🌐 Autenticación por SSH

1. Generar llave SSH (si no existe):

```bash
ssh-keygen -t ed25519 -C "tu_email@example.com"
```

2. Agregar la clave pública a tu cuenta de GitHub:

   * Copia la clave con `cat ~/.ssh/id_ed25519.pub`
   * Ve a GitHub > Settings > SSH and GPG Keys

3. Usa la URL SSH en lugar de HTTPS:

```bash
git remote set-url origin git@github.com:usuario/repositorio.git
```

---

## 🔶 Ramas (branches)

| Acción                     | Comando moderno                 | Descripción                       |
| -------------------------- | ------------------------------- | --------------------------------- |
| Crear y cambiar de rama    | `git switch -c nueva-rama`      | Crea y cambia a la nueva rama.    |
| Ver ramas disponibles      | `git branch`                    | Lista todas las ramas locales.    |
| Cambiar de rama            | `git switch nombre-rama`        | Cambia a la rama indicada.        |
| Subir rama por primera vez | `git push -u origin nueva-rama` | Sube y vincula la rama al remoto. |
| Fusionar ramas             | `git merge nombre-rama`         | Trae los cambios de otra rama.    |

---

## 🚀 Flujo de trabajo (Workflow)

1. Crea una rama:

```bash
git switch -c nueva-funcionalidad
```

2. Haz cambios y commits en esa rama.
3. Sube tu rama:

```bash
git push -u origin nueva-funcionalidad
```

4. Abre un Pull Request en GitHub.
5. El equipo revisa y aprueba la fusión.
6. La rama se fusiona en `main` (o la rama correspondiente).

---

## 🔎 Git Pull vs Git Fetch

| Comando     | Descripción                                    |
| ----------- | ---------------------------------------------- |
| `git fetch` | Descarga cambios remotos sin aplicarlos.       |
| `git pull`  | Descarga y aplica (merge) los cambios remotos. |

> Recomendado: usar `fetch` seguido de `merge` para tener control total.

---

## ⚔️ Conflictos y Resolución

Cuando hay conflictos:

1. Haz `git pull origin main` en tu rama de trabajo.
2. Git avisará de los archivos en conflicto.
3. Edita los archivos para resolver manualmente.
4. Una vez resuelto:

```bash
git add archivo-resuelto.txt
git commit
```

---

## 🔠 Git Stash

Guarda cambios temporales:

```bash
git stash
```

Recupera los cambios:

```bash
git stash pop
```

---

## 💡 Git Rebase vs Merge

| Comando      | Descripción                                                      |
| ------------ | ---------------------------------------------------------------- |
| `git merge`  | Junta ramas manteniendo el historial original.                   |
| `git rebase` | Aplica los commits de una rama sobre otra. Historial más limpio. |

---

## ⏪ Revertir cambios

| Acción                      | Comando                                 |
| --------------------------- | --------------------------------------- |
| Volver a un commit anterior | `git revert [commit]`                   |
| Revertir varios commits     | `git revert --no-commit [commit]..HEAD` |

---

## 🔄 Clonar todas las ramas

Por defecto solo se clona la rama principal. Para traer todas:

```bash
for branch in $(git branch -r | grep -v '\->'); do
    git branch --track "${branch#origin/}" "$branch"
done
git fetch --all
git pull --all
```

---

## 📁 Actualizar archivo en todas las ramas

```bash
git checkout master
git pull origin master

for branch in $(git branch --format='%(refname:short)' | grep -v 'master'); do
  git checkout $branch
  git checkout master -- README.md
  git add README.md
  git commit -m "Update README.md from master"
  git push origin $branch
done

git checkout master
```

---

## 🔧 Eliminar ramas y repositorios

* Borrar rama local:

```bash
git branch -D nombre-rama
```

* Borrar rama remota:

```bash
git push origin --delete nombre-rama
```

* Borrar repositorio: desde **Settings > Danger Zone** en GitHub.

---

## 🚪 Fork

Un *fork* es una copia de un repositorio ajeno a tu cuenta. Permite:

* Probar cambios libremente.
* Hacer Pull Requests al repositorio original para sugerir cambios.

---

## 📊 Recomendación final

Para flujos de trabajo modernos, se recomienda:

* Usar `git switch` en vez de `checkout`
* Usar `fetch` antes de `pull` si trabajas en equipo
* Configurar acceso por SSH para evitar problemas con contraseñas
* Documentar cada commit con mensajes claros

---

🌟 Este documento está en constante mejora. Puedes contribuir a su actualización con una Pull Request o Issue.
