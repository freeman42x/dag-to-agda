# .dag to .agda converter

[.dag file format](man42x/dag-file-format)

[.agda programming language](https://agda.readthedocs.io/en/v2.6.0.1/getting-started/what-is-agda.html)

The .dag structure needs to be mapped to Agda functions.

Example

```
CEO
	Operations
		Logistics
			Manager1
		Manufacturing
			Manager2
				Supervisor
	Sales
		Domestic
			Manager3
CFO
	Sales
		International
			Manager4
	Operations
HR
	Manager3
		TeamLead
```

converts to

```agda
-- CEO hierarchy
ceo : Operations -> Ceo
ceo = ?

operations : Logistics -> Operations
operations = ?

logistics : Manager1 -> Logistics
logistics = ?

manufacturing : Manager2 -> Manufacturing
manufacturing = ?

manager2 : Supervisor -> Manager2
manager2 = ?

-- Sales hierarchy under CEO
salesCeo : Domestic -> Sales
salesCeo = ?

domesticCeo : Manager3 -> Domestic
domesticCeo = ?

-- CFO hierarchy
cfo : Sales -> CFO
cfo = ?

internationalCfo : Manager4 -> International
internationalCfo = ?

operationsCfo : Operations -> CFO
operationsCfo = ?

salesCfo : International -> Sales
salesCfo = ?

-- HR hierarchy
hr : Manager3 -> HR
hr = ?

manager3Hr : TeamLead -> Manager3
manager3Hr = ?
```