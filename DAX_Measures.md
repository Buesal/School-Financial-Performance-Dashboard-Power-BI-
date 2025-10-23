# 📐 DAX Measures — School Financial Dashboard (GR)

---

## 🧮 1) Basic KPIs

```DAX
Αριθμο Εγγραφες =
COUNTROWS ( 'Εγγραφες' )

Εσοδα =
SUM ( 'Πληρωμη Μαθητων'[Ποσό Μαθητή] )

Έξοδα =
SUM ( 'Αλλες Πληρωμες'[Καθαρή Αξία Προϊόντος/Υπηρεσίας] )

Κερδος =
[Εσοδα] - [Έξοδα]

## 📆 2) Last year's performance (LY)

Αριθμο εγγραφες LY =
CALCULATE (
    [Αριθμο Εγγραφες],
    SAMEPERIODLASTYEAR ( 'Calendar'[Date] )
)

Εσοδα LY =
CALCULATE (
    [Εσοδα],
    SAMEPERIODLASTYEAR ( 'Calendar'[Date] )
)

Εξοδα LY =
CALCULATE (
    [Έξοδα],
    SAMEPERIODLASTYEAR ( 'Calendar'[Date] )
)

Κερδος LY =
CALCULATE (
    [Κερδος],
    SAMEPERIODLASTYEAR ( 'Calendar'[Date] )
)

## 📊 3) Comparison with last year (YoY, %)

Αριθμο εγγ % LY =
VAR Curr = [Αριθμο Εγγραφες]
VAR LY   = [Αριθμο εγγραφες LY]
RETURN
    DIVIDE ( Curr - LY, LY, 0 )

Έσοδα % LY =
VAR Curr = [Εσοδα]
VAR LY   = [Εσοδα LY]
RETURN
    DIVIDE ( Curr - LY, LY, 0 )

Εξοδα & LY =
VAR Curr = [Έξοδα]
VAR LY   = [Εξοδα LY]
RETURN
    DIVIDE ( Curr - LY, LY, 0 )

Κέρδος % LY =
VAR Curr = [Κερδος]
VAR LY   = [Κερδος LY]
RETURN
    DIVIDE ( Curr - LY, LY, 0 )


