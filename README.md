DELIMITER //

CREATE FUNCTION calcular_costo(
    Hora_Entrada DATETIME,
    Hora_Salida DATETIME,
    Tarifa DECIMAL(10, 2)
)
RETURNS DECIMAL(10, 2)
DETERMINISTIC
BEGIN
    DECLARE Tiempo_Total DECIMAL(10, 2);
    DECLARE Costo_Total DECIMAL(10, 2);
  
-- Calcular el tiempo total en horas
SET Tiempo_Total = TIMESTAMPDIFF(MINUTE, Hora_Entrada, Hora_Salida) / 60.0;
  
-- Calcular el costo total
SET Costo_Total = Tiempo_Total * Tarifa;
  
RETURN Costo_Total;

END //

DELIMITER ;
