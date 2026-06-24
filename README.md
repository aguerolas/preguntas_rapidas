# executive

El script contiene dos operaciones:

	1.	UPDATE sobre la tabla HBCSF.PARAMETER: Actualiza el campo starting_date del grupo PUSH_NOTIFICATION con el valor 20260531. El WHERE es de doble condición, garantizando que solo impacta un registro específico.
	2.	INSERT en la tabla HBCSF.VERSION_DETAILS: Registra la versión 3.3.1 de la app Android (AND) con API v2 y NEEDS_UPDATE = 0 (no requiere actualización forzada).