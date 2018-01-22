# State Pattern

## Definition
Erlaubt einem Objekt, sein Verhalten selbständig zu ändern, wenn sich sein interner Zustand ändern soll.

## Aufbau
Zunächst wird ein Objekt benötigt, welches verschiedene Status besitzt.
In diesem Beispiel ist es eine Ampel, welche den Status **Rot** und **Grün** besitzen kann.
Desweiteren benötigt das Objekt Funktionen zum Verändern des Zustandes, in diesem Fall das **Schalten**.
Dieses Objekt, bzw. die Funktionen können dann beliebig erweitert werden.
Ein Konto hat z.B. ein Besitzer der sich ändern kann und einen Geldbetrag.

## Code

### Status Klassen

#### Vorgabe der Status Funktionen durch abstract
```csharp
abstract class Licht
{
	public abstract void Handle(Ampel aktuelleAmpel);
}
```

#### Definition Status und Aktion die durchgeführt werden soll
```csharp
class Rot : Licht
{
	public override void Handle(Ampel aktuelleAmpel) {
		aktuelleAmpel.StatusLicht = new Gruen();
	}
}

class Gruen : Licht
{
	public override void Handle(Ampel aktuelleAmpel) {
		aktuelleAmpel.StatusLicht = new Rot();
	}
}
```

### Objekt mit verschiedenen Status
```csharp
abstract class Licht
class Ampel
{
	//Aktueller Status
	private Licht _statusLicht;
	
	//Initialisierung
	public Ampel (Licht DefaultLicht) {
		this._statusLicht = DefaultLicht;
	}
	
	// Get / Set aktueller Status + Ausgabe von neuen Wert
	public Licht StatusLicht {
		get { return _statusLicht; }
		set { 
			this._statusLicht = value;
			Console.WriteLine("Ampel Farbe: " + _statusLicht.GetType().Name);
		}
	}
	
	public void Schalte()
	{
		this._statusLicht.Handle(this);
	}
}
```

### Beispiel Main Aufruf
```csharp
Ampel Fussgaenger = new Ampel(new Rot());  

Fussgaenger.Schalte();
Fussgaenger.Schalte();
```