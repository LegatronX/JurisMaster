# 📑 Guide de Citation JurisMaster

Pour que Kimi puisse enrichir chaque leçon, voici le template de citation et de boîte à outils qu'il doit intégrer en bas de chaque page de cours.

---

### Template de "Boîte à Outils Finale" (à intégrer dans le `<footer>` des leçons)

```html
<section class="mt-24 p-12 bg-slate-900 text-white rounded-[3rem] overflow-hidden relative">
    <div class="relative z-10 text-left">
        <h3 class="text-2xl font-bold mb-6">Prêt pour l'examen ?</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
            <div>
                <h4 class="text-blue-400 font-bold text-xs uppercase mb-4 tracking-widest">Citation à retenir</h4>
                <p class="text-slate-300 italic mb-4">"[Insérer une citation majeure d'un auteur ou d'un arrêt]"</p>
                <p class="text-xs text-slate-500">— [Source de la citation]</p>
            </div>
            <div class="space-y-4">
                <button onclick="copyCitation()" class="w-full py-3 px-6 bg-white/10 hover:bg-white/20 rounded-xl border border-white/10 text-sm font-bold transition flex justify-between items-center">
                    Citer cette leçon (Zotero/APA)
                    <span>📋</span>
                </button>
                <button onclick="window.print()" class="w-full py-3 px-6 bg-blue-600 hover:bg-blue-700 rounded-xl text-sm font-bold transition flex justify-between items-center">
                    Générer la version PDF/Print
                    <span>🖨️</span>
                </button>
            </div>
        </div>
    </div>
    <div class="absolute right-[-30px] bottom-[-30px] text-[12rem] opacity-5">⚖️</div>
</section>

<script>
    function copyCitation() {
        const citation = "JurisMaster, '[Titre de la leçon]', par [Auteur/Kimi], 2026. Disponible sur : " + window.location.href;
        navigator.clipboard.writeText(citation);
        alert("Citation copiée dans le presse-papier !");
    }
</script>
```

---

### Instruction pour Kimi
"Kimi, en plus du contenu académique, tu dois impérativement inclure cette 'Boîte à Outils Finale' à la fin de chaque leçon. Adapte la citation majeure et le titre de la leçon pour chaque page."
