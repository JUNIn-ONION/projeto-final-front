# Releases e Versionamento Semântico

Use SemVer: MAJOR.MINOR.PATCH

Procedimento manual:
1. Criar branch release/x.y.z a partir de develop.
2. Atualizar changelog e versão (package.json).
3. Abrir PR para main e após merge:
   - git tag -a vX.Y.Z -m "vX.Y.Z"
   - git push origin main --tags
4. Criar Release no GitHub (Draft) e publicar.

Automação:
- Recomenda-se usar `semantic-release` no workflow para automatizar versionamento e changelog.
