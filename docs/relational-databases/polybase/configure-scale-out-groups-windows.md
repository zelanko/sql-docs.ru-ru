---
title: Улучшение масштабируемых групп PolyBase в Windows | Документация Майкрософт
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: polybase
ms.topic: tutorial
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3041a862639c8cbd71f2ad71378e980ec0b31fdc
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2018
ms.locfileid: "48905138"
---
# <a name="improve-polybase-scale-out-groups-on-windows"></a>Улучшение масштабируемых групп PolyBase в Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается настройка [масштабируемой группы PolyBase](polybase-scale-out-groups.md) в Windows. Эта группа позволяет создавать кластеры экземпляров SQL Server для обработки больших наборов данных из внешних источников данных (например, Hadoop или хранилища BLOB-объектов Azure), используя возможности масштабирования. Это помогает повысить производительность запросов.

## <a name="prerequisites"></a>предварительные требования
  
- Более одного компьютера, размещенного в одном домене.  
  
- Доменная учетная запись для запуска служб PolyBase.  
  
## <a name="process-overview"></a>Общие сведения о процессе

Ниже представлена обобщенная процедура создания масштабируемой группы PolyBase. В следующем разделе приводится более подробное пошаговое руководство.
  
1. Установите одну и ту же версию SQL Server с PolyBase на все доступные компьютеры (N).
  
2. Выберите один экземпляр SQL Server в качестве головного узла. Головным узлом можно назначить только экземпляр с установленным SQL Server Enterprise.
  
3. Добавьте в группу остальные экземпляры SQL Server в качестве вычислительных узлов с помощью [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).

4. Для мониторинга узлов группы используйте инструкцию [sys.dm_exec_compute_nodes (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).

5. Необязательный параметр. Для удаления вычислительных узлов используйте инструкцию [sp_polybase_leave_group (Transact-SQL)](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).

## <a name="example-walk-through"></a>Пошаговое руководство с примерами

В этом руководстве мы настроим группу PolyBase, используя следующие ресурсы.  
  
1. Два компьютера в домене *PQTH4A* со следующими именами:  
  
   - PQTH4A-CMP01  
  
   - PQTH4A-CMP02  
  
2. Учетная запись домена: *PQTH4A\PolybaseUser*  

## <a name="install-sql-server-with-polybase-on-all-machines"></a>Установка SQL Server с PolyBase на всех компьютерах

1. Запустите Setup.exe.
  
2. На странице выбора компонентов выберите пункт **Служба запросов PolyBase для внешних данных**.
  
3. На странице "Конфигурация сервера" настройте ядро SQL Server PolyBase и службы перемещения данных SQL Server PolyBase для запуска под **доменной учетной записью** PQTH4A\PolybaseUser.
  
4. На странице настройки PolyBase включите параметр **Использовать экземпляр SQL Server как часть масштабируемой группы PolyBase**. Это позволит открыть брандмауэр для входящих подключений к службе PolyBase.
  
5. После завершения настройки запустите **services.msc**. Убедитесь, что запущены SQL Server, ядро PolyBase и служба перемещения данных PolyBase.
  
   ![Службы PolyBase](../../relational-databases/polybase/media/polybase-services.png "Службы PolyBase")  
  
## <a name="select-one-sql-server-as-head-node"></a>Выбор одного из серверов SQL Server в качестве головного узла  
  
По завершении установки любой из компьютеров может выполнять роль головного узла группы PolyBase. В нашем примере мы выберем в качестве головного узла MSSQLSERVER на узле PQTH4A-CMP01.
  
## <a name="add-other-sql-server-instances-as-compute-nodes"></a>Добавление в группу остальных экземпляров SQL Server в качестве вычислительных узлов  
  
1. Подключитесь к SQL Server на узле PQTH4A-CMP02.
  
2. Запустите хранимую процедуру [sp_polybase_leave_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).

   ```sql
   -- Enter head node details:
   -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';
   ```  

3. Запустите файл services.msc на вычислительном узле (PQTH4A-CMP02).
  
4. Завершите работу ядра PolyBase и перезапустите службу перемещения данных PolyBase.
  
## <a name="optional-remove-a-compute-node"></a>Необязательное действие: удаление вычислительного узла  
  
1. Подключитесь к вычислительному узлу SQL Server (PQTH4A-CMP02).
  
2. Запустите хранимую процедуру sp_polybase_leave_group.
  
    ```sql  
    EXEC sp_polybase_leave_group;  
    ```  
  
3. Запустите файл services.msc на вычислительном узле, который хотите удалить (PQTH4A-CMP02).
  
4. Запустите ядро PolyBase. Перезапустите службу перемещения данных PolyBase.
  
5. Убедитесь, что узел удален, запустив на узле PQTH4A-CMP01 динамическое административное представление sys.dm_exec_compute_nodes. Теперь узел PQTH4A-CMP02 будет функционировать как автономный головной узел.  
  
## <a name="next-steps"></a>Следующие шаги  

Дополнительные сведения об устранении неполадок см. в статье [PolyBase troubleshooting with dynamic management views](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80).
  
Дополнительные сведения см. в статье [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md).
