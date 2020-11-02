Удаляет существующую, определяемую пользователем группу рабочей нагрузки регулятора ресурсов.

:::image type="icon" source="../database-engine/configure-windows/media/topic-link.gif"::: [Синтаксические обозначения в Transact-SQL](../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Синтаксис

```syntaxsql
DROP WORKLOAD GROUP group_name
[;]
```

## <a name="arguments"></a>Аргументы

*group_name*  — имя существующей определяемой пользователем группы рабочей нагрузки.

## <a name="remarks"></a>Remarks

Использование инструкции DROP WORKLOAD GROUP не допускается для внутренней группы или группы по умолчанию регулятора ресурсов.

При выполнении инструкций DDL рекомендуется иметь представление о состояниях регулятора ресурсов. Дополнительные сведения см. в разделе [Resource Governor](../relational-databases/resource-governor/resource-governor.md) (Регулятор ресурсов).

Если группа рабочей нагрузки содержит активные сеансы, удаление или перемещение этой группы в другой пул ресурсов завершится неудачно при вызове инструкции ALTER RESOURCE GOVERNOR RECONFIGURE для применения изменения. Во избежание этой проблемы можно предпринять одно из следующих действий.

- Подождать, пока все сеансы затронутых групп завершатся, и заново выполнить инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.

- Явно остановить сеанс в затронутой группе, используя команду KILL, и затем заново выполнить инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.

- Перезапустите сервер. После завершения процесса перезапуска удаленная группа не будет создана, а перемещенная группа будет использовать новое назначение пула ресурсов.

- Если при выполнении сценария с инструкцией DROP WORKLOAD GROUP решено не останавливать сеанс явно для применения изменений, то можно создать заново группу, используя то же имя для нее, которое она имела до объявления оператора DROP, и потом переместить группу в исходный пул ресурсов. Чтобы применить изменения, выполните инструкцию ALTER RESOURCE GOVERNOR RECONFIGURE.

## <a name="permissions"></a>Разрешения

Необходимо разрешение CONTROL SERVER.

## <a name="examples"></a>Примеры

В следующем примере удаляется группа рабочей нагрузки с именем `adhoc`.

```
DROP WORKLOAD GROUP adhoc;
GO
ALTER RESOURCE GOVERNOR RECONFIGURE;
GO
```

## <a name="see-also"></a>См. также:

- [Регулятор ресурсов](../relational-databases/resource-governor/resource-governor.md)
- [CREATE WORKLOAD GROUP (Transact-SQL)](../t-sql/statements/create-workload-group-transact-sql.md)  
- [ALTER WORKLOAD GROUP (Transact-SQL)](../t-sql/statements/alter-workload-group-transact-sql.md)
- [CREATE RESOURCE POOL (Transact-SQL)](../t-sql/statements/create-resource-pool-transact-sql.md)
- [ALTER RESOURCE POOL (Transact-SQL)](../t-sql/statements/alter-resource-pool-transact-sql.md)
- [DROP RESOURCE POOL (Transact-SQL)](../t-sql/statements/drop-resource-pool-transact-sql.md)
- [ALTER RESOURCE GOVERNOR (Transact-SQL)](../t-sql/statements/alter-resource-governor-transact-sql.md)  