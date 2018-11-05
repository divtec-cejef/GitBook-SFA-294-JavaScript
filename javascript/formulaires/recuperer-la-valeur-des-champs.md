# Récupérer la valeur des champs

## Liste déroulantes

```markup
<label for="pays">Sélectionnez un pays</label>
<select name="pays" id="pays">
   <option selected value="">-- Sélectionnez un pays --</option>
   <option value="FR">France</option>
   <option value="IT">Italie</option>
   <option value="CH">Suisse</option>
</select>
<button>OK</button>

<script>
document.querySelector("button").addEventListener("click", function(event) {
   //Récupère la valeur de l'option sélectionnée
   let nomPays = document.getElementById("pays").value;
   
   //Si valeur vide
   if(nomPays === "") {
      alert("Sélectionnez un pays !");
      return false;
   }
   
   alert("Pays: " + nomPays);
});
</script>
```



