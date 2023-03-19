<html>
 
<body>
 
 \SingleHeader{M\_Part\_Trans}
\MACHINE{M\_Part\_Trans}{}{C\_Part\_Proc\_Trans}{}
\VARIABLES{
	\Variable{partition\_mode}{}
}
\INVARIANTS{
	\Invariant{inv\_part\_mode}{false}{$partition\_mode \in{} PARTITIONS \tfun{} PARTITION\_MODES$}{}
}
\EVENTS{
\INITIALISATION{false}{}{
	\ACTIONS{false}{
		\Action{act001}{$partition\_mode \bcmeq{} PARTITIONS \cprod{} \{PM\_COLD\_START\}$}{true}{}
	}
}
\EVT{partition\_mode\_transition}{false}{ordinary}{}{}{
	\ANY{
		\Param{part}{true}{}
		\Param{newm}{true}{}
	}
	\GUARDS{true}{
		\Guard{grd001}{false}{$part \in{} PARTITIONS$}{true}{}
		\Guard{grd002}{false}{$newm \in{} PARTITION\_MODES$}{true}{}
		\Guard{grd003}{false}{$partition\_mode(part) = PM\_IDLE \limp{} newm = PM\_WARM\_START \lor{} newm = PM\_COLD\_START$}{true}{}
		\Guard{grd004}{false}{$partition\_mode(part) = PM\_COLD\_START \limp{} newm = PM\_IDLE \lor{} newm = PM\_COLD\_START \lor{} newm = PM\_NORMAL$}{true}{}
		\Guard{grd005}{false}{$partition\_mode(part) = PM\_WARM\_START \limp{} newm = PM\_IDLE \lor{} newm = PM\_COLD\_START \lor{} newm = PM\_WARM\_START \lor{} newm = PM\_NORMAL$}{true}{}
		\Guard{grd006}{false}{$partition\_mode(part) = PM\_NORMAL \limp{} newm = PM\_IDLE \lor{} newm = PM\_COLD\_START \lor{} newm = PM\_WARM\_START$}{true}{}
	}
	\ACTIONS{true}{
		\Action{act001}{$partition\_mode(part) \bcmeq{} newm$}{true}{}
	}
}
}
 
 <\body>
  
</html>

