< [Documentation](../../Readme.md) / [Modding](../Readme.md) / [Bonus Format](../Bonus_Format.md) / Bonus Types

The bonuses were grouped according to their original purpose. The bonus system allows them to propagate freely betwen the nodes, however they may not be recognized properly beyond the scope of original use.

# General-purpose bonuses

### NONE

Special bonus that gives no effect

### MORALE

Changes morale of affected units

- val: change in morale

### LUCK

Changes luck of affected units

- val: change in luck

### MAGIC_SCHOOL_SKILL

Changes mastery level of spells of affected heroes and units. Examples are magic plains terrain and magic school secondary skills

- subtype: school of magic
- val: level

### DARKNESS

On each turn, hides area in fog of war around affected town for all players other than town owner

- val: radius in tiles

# Hero bonuses

### MOVEMENT

Increases amount of movement points available to affected hero on new turn

- subtype: 
- - heroMovementLand: only land movement will be affected
- - heroMovementSea: only sea movement will be affected
- val: number of movement points (100 points for a tile)

### WATER_WALKING

Allows movement over water for affected heroes

- val: TODO

### FLYING_MOVEMENT

Allows flying movement for affected heroes

- val: TODO

### NO_TERRAIN_PENALTY

Eliminates terrain penalty on certain terrain types for affected heroes (Nomads ability).

- subtype: type of terrain

### PRIMARY_SKILL

Changes selected primary skill for affected heroes and units

- subtype: primary skill
- additional info: 1 - only for melee attacks, 2 - only for ranged attacks

### SIGHT_RADIUS

Reveal area of fog of war around affected heroes when hero is recruited or moves

- val: radius in tiles

### MANA_REGENERATION

Restores specific amount of mana points for affected heroes on new turn

- val: amount of spell points to restore

### FULL_MANA_REGENERATION

Restores entire mana pool for affected heroes on new turn

### NONEVIL_ALIGNMENT_MIX

Allows mixing of creaturs of neutral and good factions in affected armies without penalty to morale

### SURRENDER_DISCOUNT

Changes surrender cost for affected heroes

- val: decrease in cost, in precentage

### IMPROVED_NECROMANCY

TODO: Determine units which is raised by necromancy skill.

- subtype: creature raised
- val: Necromancer power
- addInfo: limiter by Necromancer power
- Example (from Necromancy skill):

` "power" : {`  
`  "type" : "IMPROVED_NECROMANCY",`  
`  "subtype" : "creature.skeleton",`  
`  "addInfo" : 0`  
` }`

### LEARN_BATTLE_SPELL_CHANCE

Determines chance for affected heroes to learn spell casted by enemy hero after battle

- val: chance to learn spell, percentage

### LEARN_BATTLE_SPELL_LEVEL_LIMIT

Allows affected heroes to learn spell casted by enemy hero after battle

- val: maximal level of spell that can be learned

### LEARN_MEETING_SPELL_LIMIT

Allows affected heroes to learn spells from each other during hero exchange

- val: maximal level of spell that can be learned

### ROUGH_TERRAIN_DISCOUNT

Reduces movement points penalty when moving on terrains with movement cost over 100 points. Can not reduce movement cost below 100 points

- val: penalty reduction, in movement points per tile. 

### WANDERING_CREATURES_JOIN_BONUS

Increases probability for wandering monsters to join army of affected heroes

- val: change in disposition factor when calculating join chance

### BEFORE_BATTLE_REPOSITION

Allows affected heroes to position army before start of battle (Tactics)

- val: distance within which hero can reposition his troops

### BEFORE_BATTLE_REPOSITION_BLOCK

Reduces distance in which enemy hero can reposition. Counters BEFORE_BATTLE_REPOSITION bonus

- val: distance within which hero can reposition his troops

### HERO_EXPERIENCE_GAIN_PERCENT

Increases experience gain from all sources by affected heroes

- val: additional experience bonus, percentage

### UNDEAD_RAISE_PERCENTAGE

Defines percentage of enemy troops that will be raised after battle into own army (Necromancy). Raised unit is determined by IMPROVED_NECROMANCY bonus

- val: percentage of raised troops

### MANA_PER_KNOWLEDGE

Defines amount of mana points that hero gains per each point of knowledge (Intelligence)

- val: Amount of mana points per knowledge

### HERO_GRANTS_ATTACKS

Gives additional attacks to specific creatures in affected army (Artillery)

- subtype: creature to give additional attacks
- val: number of attacks

### BONUS_DAMAGE_CHANCE

Gives specific creature in affected army chance to deal additional damage (Artillery)

- subtype: creature to give additional damage chance
- val: chance to deal additional damage, percentage

### BONUS_DAMAGE_PERCENTAGE

Defines additional damage dealt for creatures affected by BONUS_DAMAGE_CHANCE bonus (Artillery)

- subtype: creature to give additional damage percentage
- val: bonus damage, percentage

### MAX_LEARNABLE_SPELL_LEVEL

Defines maximum level of spells than hero can learn from any source (Wisdom)

- val: maximal level to learn

## Hero specialties

### SPECIAL_SPELL_LEV

Gives additional bonus to effect of specific spell based on level of creature it is casted on

- subtype: identifier of affected spell
- val: bonus to spell effect, percentage, divided by target creature level

### SPELL_DAMAGE

Gives additional bonus to effect of all spells of selected school

- subtype: affected spell school
- val: spell effect bonus, percentage

### SPECIFIC_SPELL_DAMAGE

Gives additional bonus to effect of specific spell

- subtype: identifier of affected spell
- val: bonus to spell effect, percentage

### SPECIAL_PECULIAR_ENCHANT

TODO: blesses and curses with id = val dependent on unit's level

- subtype: affected spell identifier

### SPECIAL_ADD_VALUE_ENCHANT

TODO: specialty spell like Aenin has, increased effect of spell, additionalInfo = value to add

- subtype: affected spell identifier

### SPECIAL_FIXED_VALUE_ENCHANT

TODO: specialty spell like Melody has, constant spell effect (i.e. 3 luck), additionalInfo = value to fix.

- subtype: affected spell identifier

### SPECIAL_UPGRADE

Allows creature upgrade for affected armies

- subtype: identifier of creature that can being upgraded
- addInfo: identifier of creature to which perform an upgrade

# Artifact bonuses

### SPELL_DURATION

Changes duration of timed spells casted by affected hero

- val: additional duration, turns

### SPELL

Allows affected heroes to cast specified spell, even if this spell is banned in map options or set to "special".

- subtype: spell identifier
- val: skill level mastery (0 - 3)

### SPELLS_OF_LEVEL

Allows affected heroes to cast any spell of specified level. Does not grant spells banned in map options.

- subtype: spell level, in form "spellLevelX" where X is desired level (1-5)

### SPELLS_OF_SCHOOL

Allows affected heroes to cast any spell of specified school. Does not grant spells banned in map options.

- subtype: spell school

### GENERATE_RESOURCE

Affected heroes will add specified resources amounts to player treasure on new day

- subtype: resource identifier
- val: additional daily income

### CREATURE_GROWTH

Increases weekly growth of creatures in affected towns (Legion artifacts)

- value: number of additional weekly creatures
- subtype: dwelling level, in form "creatureLevelX" where X is desired level (1-7)

### CREATURE_GROWTH_PERCENT

Increases weekly growth of creatures in affected towns

- val: additional growth, percentage

### BATTLE_NO_FLEEING

Heroes affected by this bonus can not retreat or surrender in battle

### NEGATE_ALL_NATURAL_IMMUNITIES

Negates all natural immunities for affected stacks. (Orb of Vulnerability)

- subtype:
- - immunityBattleWide: Entire battle will be affected by bonus
- - immunityEnemyHero: Only enemy hero will be affected by bonus

### OPENING_BATTLE_SPELL

In battle, army affected by this bonus will cast spell at the very start of the battle

- subtype: spell identifer
- val: spell mastery level

### FREE_SHIP_BOARDING

Heroes affected by this bonus will keep all their movement points when embarking or disembarking ship

### WHIRLPOOL_PROTECTION

Heroes affected by this bonus won't lose army when moving through whirlpool

# Creature bonuses

### STACK_HEALTH

Increases maximum hit point of affected units

- val: additional hit points to gain

### STACKS_SPEED

Increases movement speed of units in battle

- val: additional movement speed points

### CREATURE_DAMAGE

Increases base damage of creature in battle

- subtype:
- - creatureDamageMin: increases only minimal damage 
- - creatureDamageMax: increases only maximal damage
- - creatureDamageBoth: increases both minimal and maximal damage
- val: additional damage points

### SHOTS

Increases starting amount of shots that unit has in battle

- val: additional shots

# Creature abilities

## Static abilities and immunities

### NON_LIVING

Affected unit is considered to not be alive and not affected by morale and certain spells

### GARGOYLE

Affected unit is considered to be a gargoyle and not affected by certain spells

### UNDEAD

Affected unit is considered to be undead

### SIEGE_WEAPON

Affected unit is considered to be a siege machine and can not be raised, healed, have morale or move.

### DRAGON_NATURE

Affected unit is dragon. This bonus proved no effect, but is used as limiter several effects.

### KING

Affected unit will take more damage from units under Slayer spell effect

- val: required skill mastery of Slayer spell to affect this unit

### FEARLESS

Affected unit is immune to Fear ability

### NO_LUCK

Affected units can not receive good or bad luck

### NO_MORALE

Affected units can not receive good or bad morale

## Combat abilities

### FLYING

Affected unit can fly on the battlefield

- subtype:
- - movementFlying: creature will fly (slowly move across battlefield)
- - movementTeleporting: creature will instantly teleport to destination

### SHOOTER

Affected unit can shoot

### CHARGE_IMMUNITY

Affected unit is immune to JOUSTING ability

### ADDITIONAL_ATTACK

Affected unit can perform additional attacks. Attacked unit will retaliate after each attack if can

- val: number of additional attacks to perform

### UNLIMITED_RETALIATIONS

Affected unit will always retaliate if able

### ADDITIONAL_RETALIATION

Affected unit can retaliate multiple times per turn

- value: number of additional retaliations

### JOUSTING

Affected unit will deal more damage based on movement distance (Champions)

- val: additional damage per passed tile, percentage

### HATE

Affected unit will deal more damage when attacking specific creature

- subtype - identifier of hated creature
- val - additional damage, percentage

### SPELL_LIKE_ATTACK

Affected unit ranged attack will use animation and range of specified spell (Magog, Lich)

- subtype - spell identifier
- value - spell mastery level

### THREE_HEADED_ATTACK

Affected unit attacks creatures located on tiles to left and right of targeted tile (Cerberus). Only directly targeted creature will attempt to retaliate

### ATTACKS_ALL_ADJACENT

Affected unit attacks all adjacent creatures (Hydra). Only directly targeted creature will attempt to retaliate

### TWO_HEX_ATTACK_BREATH

Affected unit attacks creature located directly behind targeted tile (Dragons). Only directly targeted creature will attempt to retaliate

### RETURN_AFTER_STRIKE

Affected unit can return to his starting location after attack (Harpies)

### ENEMY_DEFENCE_REDUCTION

Affected unit will ignore specified percentage of attacked unit defence (Behemoth)

- val: amount of defence points to ignore, percentage

### GENERAL_DAMAGE_REDUCTION

Affected units will receive reduced damage from attacks by other units

- val: damage reduction, percentage
- subtype: 
- - damageTypeMelee: only melee damage will be reduced
- - damageTypeRanged: only ranged damage will be reduced
- - damageTypeAll: all damage will be reduced

### PERCENTAGE_DAMAGE_BOOST

Affected units will deal increased damage when attacking other units

- val: damage increase, percentage
- subtype: 
- - damageTypeMelee: only melee damage will increased
- - damageTypeRanged: only ranged damage will increased

### GENERAL_ATTACK_REDUCTION

Affected units will deal reduced damage when attacking other units (Blind or Paralyze spells)

- val: damage reduction, percentage

### DEFENSIVE_STANCE

Affected units will receive increased bonus to defence while defending

- val: additional bonus to defence, in skill points

### NO_DISTANCE_PENALTY

Affected unit will have no distance penalty when shooting. Does not negates wall penalties in sieges

### NO_MELEE_PENALTY

Affected ranged unit will deal full damage in melee attacks

### NO_WALL_PENALTY

Affected unit will deal full damage when shooting over walls in sieges. Does not negates distance penalty

### FREE_SHOOTING

Affected unit can use ranged attack even when blocked by enemy unit. (Sharpshooter's Bow)

### BLOCKS_RETALIATION

Affected unit will never receive retaliations when attacking

### SOUL_STEAL

Affected unit will gain new creatures for each enemy killed by this unit

- val: number of units gained per enemy killed
- subtype: 
- - soulStealPermanent: creature will stay after the battle
- - soulStealBattle: creature will be lost after the battle

### TRANSMUTATION

Affected units have chance to transform attacked unit to other creature type

- val: chance for ability to trigger, percentage
- subtype: 
- - transmutationPerHealth: transformed unit will have same HP pool as original stack, 
- - transmutationPerUnit: transformed unit will have same number of units as original stack
- addInfo: creature to transform to. If not set, creature will transform to same unit as attacker

### SUMMON_GUARDIANS

When battle starts, affected units will be surrounded from all side with summoned units

- val: amount of units to summon, per stack, percentage of summoner stack size
- subtype: identifier of creature to summon

### RANGED_RETALIATION

Affected units will retaliate against ranged attacks, if able

### BLOCKS_RANGED_RETALIATION

Affected unit will never receive counterattack in ranged attacks. Counters RANGED_RETALIATION bonus

### WIDE_BREATH

Affected unit will attack units on all hexes that surround attacked hex

### FIRST_STRIKE

Affected unit will retaliate before enemy attacks, if able

### SHOOTS_ALL_ADJACENT

Affected unit will attack units on all hexes that surround attacked hex in ranged attacks

### DESTRUCTION

Affected unit will kills additional units after attack

- val: chance to trigger, percentage
- subtype: 
- - destructionKillPercentage: kill percentage of units, 
- - destructionKillAmount: kill amount
- addInfo: amount or percentage to kill

### LIMITED_SHOOTING_RANGE

Affected unit can use ranged attacks only within specified range

- val: max shooting range in hexes
- addInfo: optional, range at which ranged penalty will trigger (default is 10)

## Special abilities

### CATAPULT

Affected unit can attack walls during siege battles

- subtype: spell that describes attack parameters

### CATAPULT_EXTRA_SHOTS

Defines spell mastery level for spell used by CATAPULT bonus
- subtype: affected spell
- val: spell mastery level to use

### MANUAL_CONTROL

Hero can control war machine affected by this bonus

- subtype: creature identifier of affected war machine
- val: chance to control unit, percentage

### CHANGES_SPELL_COST_FOR_ALLY

Affected units will decrease spell cost for their hero (Mage). If multiple units have this bonus only best value will be used

- val: reduction in mana points.

### CHANGES_SPELL_COST_FOR_ENEMY

Affected units will increase spell cost for enemy hero (Silver Pegasus). If multiple units have this bonus only best value will be used

- val: increase in mana points.

### SPELL_RESISTANCE_AURA

All units adjacent to affected unit will receive additional spell resistance bonus. If multiple adjacent units have this bonus only best value will be used

- val: additional resistance bonus, percentage

### HP_REGENERATION

Affected unit will regenerate portion of its health points on its turn

- val: amount of health points gained per round

### MANA_DRAIN

Affected unit will drain specified amount of mana points from enemy hero on each turn

val: spell points per turn to take

### MANA_CHANNELING

Affected unit will give his hero specified portion of mana points spent by enemy hero

- val: spell points to give, percentage

### LIFE_DRAIN

Affected unit will heal itself, resurrecting any dead units, by amount of dealt damage

- val: percentage of damage that will be converted into health points

### DOUBLE_DAMAGE_CHANCE

Affected unit has chance to deal double damage on attack

- val: chance to trigger, percentage

### FEAR

If enemy army has creatures affected by this bonus, they will skip their turn with 10% chance. Blocked by FEARLESS bonus.

### HEALER

Affected unit acts as healing tent and can heal allied units on each turn

- subtype: identifier of spell that will be used for healing action

### FIRE_SHIELD

When affected unit is attacked, portion of received damage will be also dealt to the attacked. Units immune to fire magic will not receive this damage. Only melee attacks will trigger this bonus

- val: amount to deal in return, percentage

### MAGIC_MIRROR

If affected unit is targeted by a spell it will reflect spell to a random enemy unit

- val: chance to trigger, percentage

### ACID_BREATH

Affected unit will deal additional damage after attack

- val - additional damage to deal, multiplied by unit stack size
- additional info: chance to trigger, percentage

### DEATH_STARE

Affected unit will kill additional units after attack

- subtype: 
- - deathStareGorgon: random amount
- - deathStareCommander: fixed amount
- val: 
- - for deathStareGorgon: chance to kill, counted separately for each unit in attacking stack, percentage. At most (stack size \* chance) units can be killed at once. TODO: recheck formula
- - for deathStareCommander: number of creatures to kill, total amount of killed creatures is (attacker level / defender level) \* val

### SPECIAL_CRYSTAL_GENERATION

If player has affected unit under his control in any army, he will receive additional 3 crystals on new week (Crystal Dragons)

### NO_SPELLCAST_BY_DEFAULT

Affected unit will not use spellcast as default attack option

## Creature spellcasting and activated abilities

### SPELLCASTER

Affected units can cast a spell as targeted action (Archangel, Faerie Dragon). Use CASTS bonus to specify how many times per combat creature can use spellcasting. Use SPECIFIC_SPELL_POWER, CREATURE_SPELL_POWER or CREATURE_ENCHANT_POWER bonuses to set spell power.

- subtype: spell identifier
- value: spell mastery level
- additional info: weighted chance to select this spell. Can be omitted for always available spells

### ENCHANTER

Affected unit will cast specified spell before his turn (Enchanter)

- val - spell mastery level
- subtype - spell identifier
- additionalInfo - cooldown before next cast, in number of turns

### RANDOM_SPELLCASTER

Affected unit can cast randomly selected beneficial spell on its turn (Master Genie)

- val - spell mastery level

### CASTS

Determines how many times per combat affected creature can cast its targeted spell

- val: number of casts available per combat

### SPELL_AFTER_ATTACK

TODO: 

- subtype - spell id
- value - chance %
- additional info - \[X, Y\]
- X - spell level
- Y = 0 - all attacks, 1 - shot only, 2 - melee only

### SPELL_BEFORE_ATTACK

TODO: 

- subtype - spell id
- value - chance %
- additional info - \[X, Y\]
- X - spell level
- Y = 0 - all attacks, 1 - shot only, 2 - melee only

### SPECIFIC_SPELL_POWER

TODO: 

- value used for Thunderbolt and Resurrection casted by units, also for Healing secondary skill (for core:spell.firstAid used by First Aid tent)
- subtype - spell id

### CREATURE_SPELL_POWER

TODO: 

- value per unit, divided by 100 (so faerie Dragons have 500)

### CREATURE_ENCHANT_POWER

TODO: 

total duration of spells casted by creature

### REBIRTH

Affected stack will resurrect after death

TODO: recheck math

- val - percent of total stack HP restored
- subtype:
- - rebirthRegular: (Phoenix)
- - rebirthSpecial: at least one unit will always resurrect (sacred Phoenix)

### ENCHANTED

Affected unit is permanently enchanted with a spell, that is cast again every turn

- subtype: spell identifier
- val: spell mastery level. If above 3, then spell has mass effect with mastery level of (val-3)

## Spell immunities

### LEVEL_SPELL_IMMUNITY

Affected unit is immune to all spell with level below or equal to value of this bonus

- val: level to which this unit is immune to

TODO: additional info?

### MAGIC_RESISTANCE

Affected unit has a chance to resist hostile spell and avoid its effects

- val: chance to trigger, percentage

### SPELL_DAMAGE_REDUCTION

Affected unit receives decreased damage from spells of specific school (Golems)

- val: reduction to damage, percentage
- subtype - spell school identifier

### MORE_DAMAGE_FROM_SPELL

Affected unit receives increased damage from specific spell

- val: increase to damage, percentage
- subtype: spell identifer

### MIND_IMMUNITY

Affected creature is immune to all mind spells and receives reduced damage from Mind Elemental

### SPELL_IMMUNITY

Affected unit is completely immune to effects of specific spell

- subtype: identifier of spell to which unit is immune

### SPELL_SCHOOL_IMMUNITY

Affected unit is immune to all spells of a specified spell school

- subtype: spell school to which this unit is immune to

### RECEPTIVE

Affected unit can be affected by all friendly spells even it would be normally immune to such spell.

# Spell effects

### POISON

TODO: describe

- val - max health penalty from poison possible

### SLAYER

Affected unit will deal increased damage to creatures with KING bonus

- val: skill mastery of Slayer spell, only creatures with lower or equal value of KING bonus are affected

### FORGETFULL

Affected unit has its ranged attack power reduced (Forgetfulness)

- val: if 0 or 1, damage is reduced by 50%. If greater than 1 then creature can not use ranged attacks

### NOT_ACTIVE

Affected unit can not act and is excluded from turn order (Blind, Stone Gaze, Paralyze)

- subtype: spell that caused this effect, optional

### ALWAYS_MINIMUM_DAMAGE

Affected creature always deals its minimum damage

- val: additional decrease to unit's minimum damage, points. Can not reduce damage to zero

### ALWAYS_MAXIMUM_DAMAGE

Affected creature always deals its maximum damage. If unit is also affected by ALWAYS_MINIMUM_DAMAGE then only additional bonus to damage will be applied

- val: additional increase to unit's maximum damage, points

### ATTACKS_NEAREST_CREATURE

Affected unit can not be controlled by player and instead it will attempt to move and attack nearest unit, friend or foe

### IN_FRENZY

Affected unit's defence is reduced to 0 and is transferred to attack with specified multiplier

- val: multiplier factor with which defence is transferred to attack (percentage)

### HYPNOTIZED

Affected unit is considered to be hypnotized and will be controlled by enemy player

### NO_RETALIATION

Affected unit will never retaliate to an attack (Blind, Paralyze)

# Others

### BLOCK_MAGIC_ABOVE

Blocks casting spells of the level above specified one in battles affected by this bonus

- val: level above which spellcasting is blocked

### BLOCK_ALL_MAGIC

Blocks casting of all spells in battles affected by this bonus

### GENERAL_DAMAGE_PREMY

Affected unit will deal more damage in all attacks (Adela specialty)

- val: additional damage, percentage

### DISGUISED

Affected heroes will be under effect of Disguise spell, hiding some of their information from opposing players

- val: spell mastery level

### VISIONS

Affected heroes will be under effect of Visions spell, revealing information of enemy objects in specific range

- val: multiplier to effect range. Information is revealed within (val \* hero spell power) range
- subtype:
- - visionsMonsters: reveal information on monsters, 
- - visionsHeroes: reveal information on heroes, 
- - visionsTowns: reveal information on towns

### BLOCK_MAGIC_BELOW

Blocks casting spells of the level below specified one in battles affected by this bonus

- val: level below which spellcasting is blocked

### BIND_EFFECT

Dummy bonus that acts as marker for Dendroid's Bind ability

### SYNERGY_TARGET

Dummy skill for alternative upgrades mod

### TOWN_MAGIC_WELL

Internal bonus, do not use

### LEVEL_COUNTER

Internal bonus, do not use

