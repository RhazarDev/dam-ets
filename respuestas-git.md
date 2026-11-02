# Respuestas del cuestionario de Git

Práctica **dam-ets** · Entornos de Desarrollo (DAM)

---

## 1. ¿Qué diferencia existe entre `git add` y `git commit`?

`git add` mete los cambios en la zona de preparación (staging), o sea, elijo qué quiero guardar. `git commit` guarda de verdad esos cambios en el historial local con un mensaje.

## 2. ¿Qué hace `git push` y por qué puede ser rechazado?

Sube mis commits locales al repositorio de GitHub. Me lo pueden rechazar si el remoto tiene commits nuevos que yo no tengo todavía, porque mi copia está desactualizada.

## 3. ¿En qué se diferencian `git fetch` y `git pull`?

`git fetch` solo se baja la información del remoto, pero no toca mis archivos. `git pull` hace fetch y además integra los cambios en mi rama, así que sí modifica mi código.

## 4. ¿Qué significa `origin/main`?

Es mi copia local de cómo estaba la rama `main` de GitHub (`origin`) la última vez que hice `fetch`. Sirve para comparar mi trabajo con el remoto.

## 5. ¿Qué muestra `git status` antes y después de `git add`?

- **Antes:** el archivo aparece como modificado o sin seguimiento, en "Changes not staged for commit" (rojo).
- **Después:** pasa a "Changes to be committed" (verde), listo para el commit.

## 6. ¿Para qué sirve `git diff --cached`?

Para ver los cambios que ya están preparados con `git add`, es decir, lo que se va a guardar en el próximo commit. `git diff` a secas solo enseña los cambios que aún no he preparado.

## 7. ¿Qué indica `git log --oneline HEAD..origin/main`?

Muestra los commits que están en el remoto y que yo todavía no tengo en local. Si no sale nada, estoy al día. Si sale algo, me toca hacer `pull`.

## 8. ¿Por qué conviene realizar commits pequeños y descriptivos?

Porque así es más fácil ver qué se hizo en cada paso, encontrar errores y deshacer algo concreto sin perder lo demás. Además, el historial se entiende mejor (por ejemplo, `docs: ampliar conceptos unidad 01` en vez de `cambios`).

## 9. ¿Cómo resolviste el `push` rechazado y por qué no utilizaste `--force`?

Lo provoqué a propósito en la segunda copia (`dam-ets-equipo2`): la primera copia ya había publicado un commit y la segunda no lo tenía. Lo resolví así:

```bash
git fetch origin
git log --oneline HEAD..origin/main
git diff HEAD origin/main
git pull --no-rebase origin main
git status
git push origin main
```

Primero miré qué había nuevo en el remoto, luego hice `pull --no-rebase` para integrarlo con un commit de merge y después ya pude hacer `push`. No usé `--force` porque pisa lo que hay en GitHub y podría borrar commits de otra copia o de otra persona. Lo correcto es integrar los cambios, no sobrescribirlos.

## 10. ¿Qué diferencia hay entre un diagrama de clases y un diagrama de secuencia?

El de clases es estructural: enseña las clases, sus atributos, métodos y cómo se relacionan. El de secuencia es de comportamiento: enseña cómo se mandan mensajes los objetos a lo largo del tiempo, paso a paso.

> No hemos dado esto en clase creo, así que he respondido mirando por google y usando IA.

## 11. ¿Qué utilidad tienen los breakpoints durante una depuración?

Paran la ejecución en una línea concreta para poder mirar el valor de las variables y avanzar paso a paso. Así veo exactamente dónde falla el programa.

> No hemos dado esto en clase creo, así que he respondido mirando por google y usando IA.

## 12. ¿Por qué son importantes las pruebas antes y después de refactorizar?

Refactorizar cambia el código por dentro, pero no debería cambiar lo que hace. Si pruebo antes y después, compruebo que el comportamiento sigue siendo el mismo y que no he roto nada.

> No hemos dado esto en clase creo, así que he respondido mirando por google y usando IA.

## 13. ¿En qué carpeta y ventana de IntelliJ estabas cuando se rechazó el `push`?

Estaba en la carpeta `~/git/dam-ets-equipo2` (la segunda copia del repositorio), en la ventana de IntelliJ que abrí con para `dam-ets-equipo2`. Lo hice desde la terminal Bash integrada.