Wird verwendet um symmetrischen Schlüssel (AES: berühmteste symmetrische Verschlüsselung Methode) über unsicheres Medium auszutauschen

#### Beispiel
Alice - Bob

**öffentliche Parameter** (darf jeder kennen)
$p ... große Primzahl$
$g ∈ \{1,2,3,..., p -1\}$

Beide generieren einen öffentlichen und einen privaten "Schlüssel"
**Alice**
$$a=K_{PrivA} ϵ \{2,3,...,p−2\}$$
$$A = K_{PubA} ≡ g^a \mod p$$
**Bob**
$$b=K_{PrivB} ϵ \{2,3,...,p−2\}$$
$$B = K_{PubB} ≡ g^b \mod p$$

Beide schicken ihren öffentlichen "Schlüssel" (A und B) über das unsicher Medium und berechnen dann aus dem erhaltenem "Schlüssel" und ihrem privaten "Schlüssel", den tatsächlichen Schlüssel für eine symmetrische Verschlüsselung

$$ K_{AB} = B^a \mod p $$
$$ K_{AB} = A^b \mod p $$

