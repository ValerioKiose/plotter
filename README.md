# Επαναχρησιμοποίηση inkjet εκτυπωτή ως καρτεσιανό παντογράφο

Μετατροπή χαλασμένου εκτυπωτή σε ένα ικανοποιητικά λειτουργικό παντογράφο χωρίς την ανάγκη αγοράς ακριβού υλικού όπως γραμμικές ράγες ακριβείας και βηματικούς κινητήρες, ένας μέσος εκτυπωτής αποτελείται ήδη από DC κινητήρες, οπτικούς κωδικοποιητές και πλαίσιο με γραμμικές ράγες, ακριβώς ότι χρειάζεται και ένας παντογράφος για να λειτουργήσει. Με την χρήση ενός STM32 και του ανοιχτού κώδικα GRBL μπορούμε να χειριστούμε τον εκτυπωτή όπως εμείς θέλουμε και σαν αποτέλεσμα να έχουμε ένα μηχάνημα που κινείται με μεγαλύτερη ακρίβεια και ταχύτητα από ότι προσφέρει η φύση των βηματικών κινητήρων.

![1000003504](https://github.com/user-attachments/assets/9dc03962-012e-44f6-9188-87ff08456a34)
![1000003500](https://github.com/user-attachments/assets/7fc31d36-9656-4980-bd9d-e4c50efd3938)


## Πως ΘΑ λειτουργεί

Ένας μηχανισμός καρτεσιανής κίνησης επιτρέπει σε ένα μηχάνημα να κινείται με ευχέρεια σε 3 διαστάσεις, πάνω – κάτω, δεξιά – αριστερά, εμπρός – πίσω, οι κινήσεις αυτές γίνονται κατά μήκος των αξόνων X, Y και Ζ, αυτό είναι η βασική αρχή λειτουργίας των περισσότερων CNC και παντογράφων. Στην παρούσα περίπτωση κάθε άξονας από τους Χ, Υ και Ζ θα ελέγχεται ανεξάρτητα, επιτρέποντας στο παντογράφο να φτάνει σε οποιοδήποτε σημείο της επιφάνειας εργασίας μέσω των συνδυασμένων κινήσεων όλων των αξόνων. 

Ο παντογράφος θα λειτουργεί με τη χρήση κινητήρων συνεχούς ρεύματος (DC) οι οποίοι ελέγχονται μέσω οδηγούς τύπου H-bridge (BTS7960), παράλληλα οι οπτικοί κωδικοποιητές θα δίνουν άμεση ανατροφοδότηση για τη θέση των κινητήρων στον κάθε άξονα. Οι λειτουργίες θα τρέχουν σε ένα STM32 το οποίο διαδέχθηκε γιατί διαβάζει κωδικοποιητές σε επίπεδο υλικού και δεν απασχολεί τον επεξεργαστή αφήνοντας έτσι χώρο για άλλες λειτουργίες του πρότζεκτ όπως την οδήγηση των κινητήρων, PIDs loops και διάβασμα εντολών από το GRBL.

Οι οδηγίες για τις κινήσεις του κάθε άξονα θα γίνονται μέσω του GRBL. Το GRBL έχει σχεδιαστεί για βηματικούς κινητήρες και δίνει παλμούς "βήματος" και "κατεύθυνσης", δηλαδή κάνε 100 βήματα με δεξιά περιστροφή. Επειδή όμως ένας DC κινητήρας δεν περιστρέφετε με βήματα, πρέπει να γίνει μια μεταγλώττιση από εισερχόμενα βήματα που πρέπει να εκτελεστούν επιτόπου, σε τελικό σημείο θέσης που πρέπει να βρίσκεται κάθε άξονας, το τελικό σημείο που όντως βρίσκεται κάθε άξονας ελέγχεται συνεχόμενα από κλειστό βρόχο και τους κωδικοποιητές. Το τελικό αποτέλεσμα θα είναι ένα γρήγορο και ακριβές μηχάνημα το οποίο θα μπορεί να καταλάβει πότε και αν κάνει λάθος στις κινήσεις του.
## Τρόπος Χρήσης

## Σχεδιάγραμμα


