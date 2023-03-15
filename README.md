# practice_task_11.5

Что необходимо сделать:

1. Требуется настроить пайплайн, который будет запускаться при изменении SQL-скрипта, хранящегося в репозитории (его выбор также на ваше усмотрение).
2. Пайплайн должен запускать изменившийся скрипт и выводить результат запроса.

Для примера предлагается два запроса:

простейший select, который будет просто выводить первую строку таблицы:

select * from fr.fram_acc limit 1;

и вторую выборку. Она будет выбирать все РНК крыс, хранящиеся в этой базе данных:

SELECT fr.rfam_acc, fr.rfamseq_acc, fr.seq_start, fr.seq_end
FROM full_region fr, rfamseq rf, taxonomy tx
WHERE rf.ncbi_id = tx.ncbi_id
AND fr.rfamseq_acc = rf.rfamseq_acc
AND tx.ncbi_id = 10116 -- NCBI taxonomy id of Rattus norvegicus
AND is_significant = 1 -- exclude low-scoring matches from the same clan

Координаты этой базы:

Parameter	Value
host	mysql-rfam-public.ebi.ac.uk
user	rfamro
password	none
port	4497
database	Rfam
Для соединения с БД можно использовать:

mysql --user rfamro --host mysql-rfam-public.ebi.ac.uk --port 4497 --database Rfam