1. Trouver tous les documents dans la collection "employees".
   db.employees.find({})

2. Trouver tous les documents où l'âge est supérieur à 33.
   db.employees.find({ age: { $gt: 33 } })

3. Trier les documents dans la collection "employees" par salaire décroissant.
   db.employees.find({}).sort({ salary: -1 })

4. Sélectionner uniquement le nom et le job de chaque document.
   db.employees.find({}, { name: 1, job: 1, \_id: 0 })

5. Compter le nombre d'employés par poste.
   db.employees.aggregate([
   { $group: { _id: "$job", total: { $sum: 1 } } }
   ])

6. Mettre à jour le salaire de tous les développeurs à 80000.
   db.employees.updateMany({ job: "Developer" }, { $set: { salary: 80000 } })

#Exo.md

Exercice 1
db.salles.find({ smac: true }, { \_id: 1, nom: 1 })

Exercice 2
db.salles.find({ capacite: { $gt: 1000 } }, { nom: 1, \_id: 0 })

Exercice 3
db.salles.find({ "adresse.numero": { $exists: false } }, { \_id: 1 })

Exercice 4
db.salles.find({ avis: { $size: 1 } }, { \_id: 1, nom: 1 })

Exercice 5
db.salles.find({ styles: "blues" }, { styles: 1, \_id: 0 })

Exercice 6
db.salles.find({ "styles.0": "blues" }, { styles: 1, \_id: 0 })

Exercice 7
db.salles.find({ "adresse.codePostal": /^84/, capacite: { $lt: 500 } }, { "adresse.ville": 1, \_id: 0 })

Exercice 8
db.salles.find({ $or: [{ \_id: { $mod: [2, 0] } }, { avis: { $exists: false } }] }, { \_id: 1 })

Exercice 9
db.salles.find({ "avis.note": { $gte: 8, $lte: 10 } }, { nom: 1, \_id: 0 })

Exercice 10
db.salles.find({ "avis.date": { $gt: new Date("2019-11-15T00:00:00Z") } }, { nom: 1, \_id: 0 })

Exercice 11
db.salles.find({ $expr: { $gt: [{ $multiply: ["$\_id", 100] }, "$capacite"] } }, { nom: 1, capacite: 1, \_id: 0 })

Exercice 13
db.salles.distinct("adresse.codePostal")

Exercice 14
db.salles.updateMany({}, { $inc: { capacite: 100 } })

Exercice 15
db.salles.updateMany({ styles: { $ne: "jazz" } }, { $push: { styles: "jazz" } })
