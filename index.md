<html>
 
dddddd
  
</html>

 <?xml version="1.0" encoding="UTF-8" standalone="no"?>
<org.eventb.core.machineFile org.eventb.core.configuration="org.eventb.core.fwd;ch.ethz.eventb.qualprob.qpConfig" version="5">
<org.eventb.core.event name="'" org.eventb.core.convergence="0" org.eventb.core.extended="false" org.eventb.core.label="INITIALISATION">
<org.eventb.core.action name="'" org.eventb.core.assignment="partition_mode ≔ PARTITIONS × {PM_COLD_START}" org.eventb.core.label="act001"/>
</org.eventb.core.event>
<org.eventb.core.seesContext name="(" org.eventb.core.target="C_Part_Proc_Trans"/>
<org.eventb.core.variable name=")" org.eventb.core.identifier="partition_mode"/>
<org.eventb.core.invariant name="*" org.eventb.core.label="inv_part_mode" org.eventb.core.predicate="partition_mode ∈ PARTITIONS → PARTITION_MODES"/>
<org.eventb.core.event ch.ethz.eventb.qualprob.probabilistic="false" name="+" org.eventb.core.convergence="0" org.eventb.core.extended="false" org.eventb.core.label="partition_mode_transition">
<org.eventb.core.parameter name="'" org.eventb.core.identifier="part"/>
<org.eventb.core.parameter name="(" org.eventb.core.identifier="newm"/>
<org.eventb.core.guard name=")" org.eventb.core.label="grd001" org.eventb.core.predicate="part ∈ PARTITIONS"/>
<org.eventb.core.guard name="*" org.eventb.core.label="grd002" org.eventb.core.predicate="newm ∈ PARTITION_MODES"/>
<org.eventb.core.guard name="+" org.eventb.core.label="grd003" org.eventb.core.predicate="partition_mode(part) = PM_IDLE ⇒ newm = PM_WARM_START ∨ newm = PM_COLD_START"/>
<org.eventb.core.guard name="," org.eventb.core.label="grd004" org.eventb.core.predicate="partition_mode(part) = PM_COLD_START ⇒ newm = PM_IDLE ∨ newm = PM_COLD_START ∨ newm = PM_NORMAL"/>
<org.eventb.core.guard name="-" org.eventb.core.label="grd005" org.eventb.core.predicate="partition_mode(part) = PM_WARM_START ⇒ newm = PM_IDLE ∨ newm = PM_COLD_START ∨ newm = PM_WARM_START ∨ newm = PM_NORMAL"/>
<org.eventb.core.guard name="." org.eventb.core.label="grd006" org.eventb.core.predicate="partition_mode(part) = PM_NORMAL ⇒ newm = PM_IDLE ∨ newm = PM_COLD_START ∨ newm = PM_WARM_START"/>
<org.eventb.core.action name="/" org.eventb.core.assignment="partition_mode(part) ≔ newm" org.eventb.core.label="act001"/>
</org.eventb.core.event>
</org.eventb.core.machineFile>
