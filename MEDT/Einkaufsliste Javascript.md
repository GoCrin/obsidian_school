# Code Analyse

loop durch alle Einkaufslisteneinträge (Eistee, Brotaufstrich, Mikrowellenpopcorn, etc.) und wenn diese keine checkbox sind wird eine checkbox hinzugefügt
```
function addCheckboxesToListItems() {  
    document.querySelectorAll('ul#einkaufsliste > li li').forEach(item => {  
        if (!item.querySelector('input[type=checkbox]')) {  
            addCheckboxToListItem(item);  
        }  
    });  
}
```

nimmt Einkaufslisteneintrag, umschließt es in \<label\>, fügt davor eine checkbox ein checkbox toggled die Klasse 'item-done'
```
function addCheckboxToListItem(item) {  
    let label = document.createElement('label');  
    let checkbox = document.createElement('input');  
    checkbox.setAttribute('type', 'checkbox');  
    checkbox.addEventListener('change', (e) => {  
        label.classList.toggle('item-done', e.target.checked);  
    });  
  
    label.appendChild(checkbox);  
    label.appendChild(document.createTextNode(item.innerText));  
  
    item.replaceChildren(label);  
}
```

baut die Auswahlmöglichkeiten beim hinzufügen von Einkaufslisteneinträgen löscht alle Auswahlmöglichkeiten, holt dann alle Kategorien von Einkaufsliste erstellt dann option mit geholtem String von Kategorien fügt option an Auswahl an
```
function buildCategoryList() {  
    let selectList = document.getElementById('kategorie-neu');  
    selectList.replaceChildren();  
  
    document.querySelectorAll('ul#einkaufsliste > li').forEach(item => {  
        let kategorie = item.querySelector('span').textContent;  
  
        let option = document.createElement('option');  
        option.textContent = kategorie;  
        option.value = item.classList[0];  
        selectList.appendChild(option);  
    });  
}
```

erstellt Einkaufslisteneintrag fügt checkbox hinzu, fügt fertigen Eintrag in Kategorie ein  
```
function createListItem(produkt, kategorieKlasse) {  
    let newItem = document.createElement('li');  
    newItem.textContent = produkt;  
    addCheckboxToListItem(newItem);  
  
    document.querySelector(`li.${kategorieKlasse} > ul`).appendChild(newItem);  
}
```
  
Erstellt Einkaufslisteneintrag wenn 'Produkt hinzufügen' gedrückt wird
```
document.getElementById('button-neu').addEventListener('click', () => {  
    createListItem(  
        document.getElementById('produkt-neu').value,  
        document.getElementById('kategorie-neu').value  
    );  
});  
  
buildCategoryList();  
addCheckboxesToListItems();
```