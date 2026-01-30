# Guide de Contribution

Merci de votre intérêt pour contribuer à ce projet! 🎉

## Code of Conduct

En participant à ce projet, vous acceptez de respecter notre [Code of Conduct](CODE_OF_CONDUCT.md).

## Comment Contribuer

### Rapporter un Bug 🐛

1. Vérifiez que le bug n'a pas déjà été rapporté dans [Issues](https://github.com/mcos12345/AS5045B-SSI-Reader---STM32F411CEU6-WeAct-Studio/issues)
2. Utilisez le template "Bug Report"
3. Incluez:
   - Description claire du problème
   - Steps to reproduce
   - Comportement attendu vs actuel
   - Screenshots si applicable
   - Environnement (version STM32CubeIDE, OS, etc.)

### Proposer une Fonctionnalité 💡

1. Ouvrez une issue avec le template "Feature Request"
2. Décrivez clairement:
   - Le problème que ça résout
   - La solution proposée
   - Les alternatives considérées

### Soumettre une Pull Request 🚀

1. **Fork** le repository
2. **Clone** votre fork
3. **Créez une branche** depuis `develop`:
```bash
   git checkout -b feature/amazing-feature
```
4. **Committez** vos changements:
```bash
   git commit -m 'Add amazing feature'
```
5. **Respectez le style de code** (voir section ci-dessous)
6. **Ajoutez des tests** si applicable
7. **Documentez** vos changements
8. **Push** vers votre fork:
```bash
   git push origin feature/amazing-feature
```
9. **Ouvrez une Pull Request** vers `develop`

## Style de Code

### C Code Style

Nous suivons le style de code STM32 standard:
```c
// ✅ GOOD
void AS5045B_Init(AS5045B_Config_t *config)
{
    if (config == NULL) {
        return HAL_ERROR;
    }
    
    // Configuration...
}

// ❌ BAD
void as5045b_init(AS5045B_Config_t* config){
    if(config==NULL)return HAL_ERROR;
}
```

**Règles:**
- Indentation: 4 espaces (pas de tabs)
- Noms de fonctions: `PascalCase` avec préfixe module
- Variables: `snake_case`
- Constantes: `UPPER_CASE`
- Accolades: Nouvelle ligne pour fonctions, même ligne pour structures de contrôle
- Commentaires: Doxygen style pour fonctions publiques

### Formattage Automatique
```bash
# Installer clang-format
sudo apt install clang-format

# Formater un fichier
clang-format -i Drivers/AS5045B/Src/as5045b_driver.c

# Formater tout le projet
make format
```

## Tests

### Exécuter les Tests
```bash
# Tests unitaires
make test-unit

# Tests d'intégration
make test-integration

# Coverage
make coverage
```

### Ajouter des Tests

Tous les nouveaux code doivent inclure des tests:
```c
// Tests/unit/test_as5045b.c
void test_AS5045B_PositionToDegrees(void)
{
    uint16_t position = 2048;  // 180°
    float degrees = AS5045B_PositionToDegrees(position);
    
    TEST_ASSERT_FLOAT_WITHIN(0.1f, 180.0f, degrees);
}
```

## Documentation

### Commenter le Code

Utilisez Doxygen pour documenter les fonctions publiques:
```c
/**
 * @brief Lit la position de l'encodeur
 * 
 * Cette fonction effectue une lecture SSI complète de l'AS5045B
 * avec vérification de parité et gestion d'erreurs.
 * 
 * @return AS5045B_Reading_t Structure contenant position et status
 * 
 * @note La fonction prend environ 15-20 µs à 1 MHz
 * @warning Doit être appelée avec interruptions activées
 * 
 * @code
 * AS5045B_Reading_t reading = AS5045B_ReadPosition();
 * if (reading.valid) {
 *     printf("Position: %d\n", reading.position);
 * }
 * @endcode
 */
AS5045B_Reading_t AS5045B_ReadPosition(void);
```

### Mettre à Jour la Documentation

- Mettez à jour `README.md` si nécessaire
- Ajoutez des exemples dans `Examples/`
- Mettez à jour `CHANGELOG.md`

## Workflow Git

### Branches

- `main`: Version stable, releases seulement
- `develop`: Développement actif
- `feature/*`: Nouvelles fonctionnalités
- `bugfix/*`: Corrections de bugs
- `hotfix/*`: Corrections urgentes pour production

### Commits

Utilisez [Conventional Commits](https://www.conventionalcommits.org/):
```
feat: Add velocity calculation
fix: Correct parity check in SSI driver
docs: Update hardware setup guide
test: Add unit tests for filters
refactor: Optimize timing loop
perf: Reduce read time by 3µs
```

## Checklist PR

Avant de soumettre une PR, vérifiez:

- [ ] Code compile sans warnings
- [ ] Tests passent (`make test`)
- [ ] Code formatté (`make format`)
- [ ] Documentation à jour
- [ ] CHANGELOG.md mis à jour
- [ ] Commits suivent convention
- [ ] Pas de fichiers générés commités

## Questions?

N'hésitez pas à:
- Ouvrir une issue "Question"
- Rejoindre notre Discord
- Envoyer un email

---

Merci de contribuer! 🙏
