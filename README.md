# inserting_temp_table_sql
DECLARE @DATAI AS DATETIME
DECLARE @DATEF AS DATETIME
DECLARE @CONT AS INT

SET @DATAI = '20130101'
SET @CONT = 0

-- CRIA TABELA TEMP PARA POPULAR COM AS SEMANAS DO ANO
--CREATE TABLE #DATAS(DATA DATETIME, WEEK_NUM INT, YEAR_MONTH INT ) 

WHILE @DATAI <= CAST(GETDATE() AS DATE)
	BEGIN
		INSERT INTO #DATAS VALUES (CAST(@DATAI AS DATE), DATEPART(ISO_WEEK, CAST(@DATAI AS DATE)), LEFT(CONVERT(VARCHAR, @DATAI, 112), 6))
		SET @CONT = @CONT + 1
		SET @DATAI = DATEADD(DAY, 1, @DATAI)
	END

SELECT * FROM #DATAS
