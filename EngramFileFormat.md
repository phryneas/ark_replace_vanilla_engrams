# Ark Engram File Format:
* Offset 0xA3: begin of string section.  
in this section, there is always a 32-bit-number describing the length of a zero-terminated string that directly follows.  
example of the contents of such a section:  
```/Game/PrimalEarth/CoreBlueprints/Engrams/EngramEntry_Fabricator
/Game/PrimalEarth/CoreBlueprints/Engrams/EngramEntry_HidePants
/Game/PrimalEarth/CoreBlueprints/Engrams/EngramEntry_ScubaPants
/Game/PrimalEarth/CoreBlueprints/Items/Armor/SCUBA/PrimalItemArmor_ScubaPants
/Script/CoreUObject
/Script/Engine
/Script/ShooterGame
ArrayProperty
bGiveBlueprintToPlayerInventory
bLegacyGeneratedClassIsAuthoritative
bLegacyNeedToPurgeSkelRefs
Blueprint
BluePrintEntry
BlueprintGeneratedClass
BlueprintGuid
BlueprintSystemVersion
BoolProperty
Class
Default__EngramEntry_ScubaPants_C
Default__PrimalEngramEntry
Engine
EngramEntries
EngramEntry_Fabricator_C
EngramEntry_HidePants_C
EngramEntry_ScubaPants
EngramEntry_ScubaPants_C
EngramRequirementSets
EntryPoint
ExecuteUbergraph_EngramEntry_ScubaPants
Function
GeneratedClass
Guid
IntProperty
None
Object
ObjectProperty
Package
ParentClass
PrimalEngramEntry
PrimalItemArmor_ScubaPants_C
RequiredCharacterLevel
RequiredEngramPoints
StructProperty
```

* Offset [value of UInt32 @0x3D]: start of a section with unknown contents
* Offset [value of UInt32 @0x49]: start of another section with interesting data:
* Offset [value of UInt32 @0x49] + 0xC0: UInt 32 with Engram Level Requirement
* Offset [value of UInt32 @0x49] + 0xDC: UInt 32 with Engram Costs