# STHDF class template 2026-2027

Toto je šablóna repozitára pre predmet **Systémové myslenie v IT a digitálna
fabrikácia** (FIIT STU). Neklonuje sa cez GitHub Classroom — každý študent si
z nej urobí **vlastný, čistý klon bez histórie** a pracuje vo svojom repozitári.

## 1. Predpoklady

- nainštalovaný [Git](https://git-scm.com/downloads)
- vlastný GitHub účet

## 2. Vytvor si vlastný klon (bez histórie)

Klonovanie tejto šablóny normálnym `git clone` by ti do repozitára prenieslo
aj celú jej históriu — to nechceme. Postav sa v termináli do priečinka,
**v ktorom** má vzniknúť tvoj projekt (napr. `~/Skola/STHDF/`) — príkaz nižšie
si `ST-042-MojeMeno` vytvorí sám ako podpriečinok. Potom spusti:

```bash
git clone --depth 1 https://github.com/06-STH-Projects/2026_sthdf_class_template.git ST-042-MojeMeno
cd ST-042-MojeMeno
rm -rf .git
git init
git add -A
git commit -m "Initial commit"
```

Výsledok: priečinok `ST-042-MojeMeno/` obsahuje celý obsah šablóny, ale ako
**nový, samostatný git repozitár s jedným commitom** — žiadna história
šablóny sa neprenáša.

> Skript, ktorý spraví presne toto isté jedným príkazom, je v
> [`tools/clone-student-template.sh`](tools/clone-student-template.sh):
> `./clone-student-template.sh ST-042-MojeMeno`

### Pomenovanie priečinka

- **Individuálna práca:** `ST-XXX-MojeMeno` (napr. `ST-042-JanNovak`)
- **Tímový projekt:** `PRJ-YYY-NazovProjektu` (napr. `PRJ-017-SmartClock`)

Toto pomenovanie (`ST-XXX` / `PRJ-YYY`) sa používa aj neskôr, keď budeš svoje
výstupy publikovať do triedneho repozitára — drž sa ho od začiatku.

## 3. Založ si vlastný repozitár na GitHube

1. Na [github.com/new](https://github.com/new) si založ **prázdny** repozitár
   (bez README, bez `.gitignore` — tie už máš z klonu).
2. Pripoj ho ako remote a pushni:

```bash
git remote add origin <URL-tvojho-noveho-repozitara>
git branch -M main
git push -u origin main
```

Odteraz pracuješ vo svojom vlastnom repozitári, nezávisle od šablóny.

> **Žiadny osobitný "školský server" neexistuje.** Repozitár z kroku 3 je
> obyčajný osobný GitHub účet — nič iné netreba zakladať. Ak GitHub účet
> ešte nemáš, založ si ho zadarmo na [github.com/join](https://github.com/join).

## 4. Publikuj výstup do triedneho repozitára

Tento predmet nepoužíva GitHub Classroom sync — tvoj repozitár je od
šablóny aj od triedneho repozitára nezávislý, takže sa tam tvoj výstup
nedostane sám. **Do triedneho repa ide len prehľad** (About Me,
Knowledge Contribution, Project Summary, Project Outcomes, Pitch, Final
Presentation, Reflexia) s odkazmi na tvoj plný repozitár — **nie celý
repozitár samotný.**

Vyučujúci ti vopred pridelí číslo `ST0XX` (roster) — triedny repozitár
už má pre teba pripravený priečinok `students/ST0XX/`. Keď je výstup
hotový:

1. Na GitHube forkni [`class_sthdf_2026-2027`](https://github.com/06-STH-Projects/class_sthdf_2026-2027)
   (tlačidlo **Fork**).
2. Naklonuj si svoj fork (toto už je normálny `git clone` — históriu
   triedneho repa tu chceš zachovať):

   ```bash
   git clone https://github.com/<tvoj-ucet>/class_sthdf_2026-2027.git
   cd class_sthdf_2026-2027
   git checkout -b submit/ST025
   ```

3. Uprav SVOJ pridelený priečinok (napr. `ST025` — použi číslo z
   rosteru), nie celý repozitár skopírovaný odinakiaľ:
   `content/docs/sk/class_sthdf_dashboard/.../students/ST025/` — doplň
   `about-me/`, `knowledge-contribution/`, `project-summary/`,
   `project-outcomes/`, `pitch-presentation/`, `final-presentation/`,
   `reflexia/` s odkazmi na tvoj plný GitHub repozitár:

   ```bash
   git add content/docs/sk/class_sthdf_dashboard/*/students/ST025
   git commit -m "submit: ST025 deliverables"
   git push -u origin submit/ST025
   ```

4. Na GitHube otvor **Pull Request** z `submit/ST025` do `main`
   triedneho repozitára.

Podrobnejšie vysvetlenie (aj prečo takto a nie inak) je v
[K000119 – Ako si vytvoriť čistý klon triedneho repozitára](https://knifes.systemthinking.sk/sk/knifes/K000119-klon-triedneho-repozitara)
(krok 6).

## 5. Čo je vnútri

| Priečinok | Obsah |
|---|---|
| `content/docs/sk/` (`en/`) | tvoj obsah — 7Ds, SDLC, Q12, STHDF, KNIFE |
| `core/` | zdieľané nástroje a automatizácia (Makefile targets, generátory) |
| `config/` | konfigurácia jednotlivých metodík |
| `publishing/docusaurus/` | Docusaurus stránka, ak si obsah chceš publikovať |

Rýchly prehľad dostupných príkazov: `make help`

## 6. Odkazy

- 🧭 Portál predmetu: [sthdf.systemthinking.sk](https://sthdf.systemthinking.sk)
- 📚 KNIFE dokumentácia: [knifes.systemthinking.sk](https://knifes.systemthinking.sk)

## License

- **Kód a skripty**: [MIT License](./LICENSE)
- **Vzdelávací obsah a dokumentácia** (`.md` súbory, metodiky, poznámky): [CC-BY 4.0 License](./LICENSE-DOCS)
