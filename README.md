# ZK_Weidu_Stuff
This contains a few functions for modders to reuse.

As of now, the available functions are related to spell creation:

* ADD_SPELL_HEADER is surprisingly missing from base WeiDU. This patch function here creates a new header which is appended to the end of existing headers of a spelll
  * Pending improvement: allow the possibility to say after which existing header this should be inserted. Currently only allows adding at the end of existing headers
* SCALE_SPELL allows scaling a spell according to the stats of the caster. It is designed to allow more flexibility for modders when designing their spells
  * Known limit: If the original ability targets "Any point within range", then the projectile targets whoever was the target of the last "layer" of scaling. This looks like an engine limitation, however I will keep investigating for a workaround
* MULTI_SCALE_SPELL is like SCALE_SPELL, except it uses a 2da and allows scaling in more than one way, depending on more than one stat
  * Pending improvement: if multiple aspects of the spell scale of one stat, then these should be done in one series of spell instead of multiple ones
* SCALE_SPELL_WITH_LEVEL allows easy scaling of as many effects of a spell as wanted, based on level and regular intervals. With a proper 2da and a spell with at least one existing ability, this can handle any basic scaling of spells depending on level (dice number, dice size, saving throw,...)

To use this, simply include ScaleSpell.tpa, the 2da and temp folders into your mod folder and add the following line to your mod before you use the functions:
INCLUDE ~%MOD_FOLDER%/ScaleSpell.TPA~
