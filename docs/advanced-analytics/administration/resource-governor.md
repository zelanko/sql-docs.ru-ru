---
title: Управление рабочими нагрузками Python и R с помощью Resource Governor
description: Узнайте, как использовать Resource Governor для управления ресурсами ЦП, физических операций ввода-вывода и выделения ресурсов памяти для рабочих нагрузок Python и R в SQL Server Службы машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/02/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 9000ab8bb15e8f9910b8b780aa38d134fa984032
ms.sourcegitcommit: af5e1f74a8c1171afe759a4a8ff2fccb5295270a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71823536"
---
# <a name="manage-python-and-r-workloads-with-resource-governor-in-sql-server-machine-learning-services"></a>Управление рабочими нагрузками Python и R с помощью Resource Governor в SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Узнайте, как использовать [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) для управления ресурсами ЦП, физических операций ввода-вывода и выделения ресурсов памяти для рабочих нагрузок Python и R в SQL Server службы машинного обучения.

Алгоритмы машинного обучения в Python и R обычно являются ресурсоемкими. В зависимости от приоритетов рабочих нагрузок может потребоваться увеличить или уменьшить количество ресурсов, доступных для Службы машинного обучения.

Дополнительные общие сведения см. в разделе [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).

> [!NOTE] 
> Resource Governor является функцией выпуска Enterprise Edition.

## <a name="default-allocations"></a>Выделения по умолчанию

По умолчанию среда выполнения внешних скриптов для машинного обучения ограничивается не более чем на 20% от общего объема памяти компьютера. Это зависит от системы, но в общем случае это ограничение не подходит для серьезных задач машинного обучения, таких как обучение модели или прогнозирование многих строк данных. 

## <a name="manage-resources-with-resource-governor"></a>Управление ресурсами с помощью Resource Governor
 
По умолчанию внешние процессы используют до 20% общего объема памяти узла на локальном сервере. Пул ресурсов по умолчанию можно изменить, чтобы внести изменения на уровне сервера, а процессы R и Python будут использовать любую емкость, доступную для внешних процессов.

Кроме того, можно создать пользовательские **Внешние пулы ресурсов**со связанными группами рабочей нагрузки и классификаторами, чтобы определить выделение ресурсов для запросов, исходящих от конкретных программ, узлов или других предоставленных вами критериев. Внешний пул ресурсов — это тип пула ресурсов, представленный в [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] , помогающий управлять процессами R и Python, внешними по отношению к ядру СУБД.

1. [Включить управление ресурсами](https://docs.microsoft.com/sql/relational-databases/resource-governor/enable-resource-governor) (по умолчанию он отключен).

2. Запустите [Создание внешнего пула ресурсов](https://docs.microsoft.com/sql/t-sql/statements/create-external-resource-pool-transact-sql) , чтобы создать и настроить пул ресурсов, а затем [измените регулятор ресурсов](https://docs.microsoft.com/sql/t-sql/statements/alter-resource-governor-transact-sql) , чтобы его реализовать.

3. Создайте группу рабочей нагрузки для детализированного выделения, например между обработкой и оценкой.

4. Создание классификатора для перехвата вызовов для внешней обработки.

5. Выполнение запросов и процедур с помощью созданных объектов.

Пошаговые инструкции см. в разделе [Создание пула ресурсов для внешних сценариев R и Python](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md) .

Общие сведения о терминологии и общих понятиях см. в разделе [Resource Governor пула ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

## <a name="processes-under-resource-governance"></a>Процессы в разделе "Управление ресурсами"
  
 *Внешний пул ресурсов* можно использовать для управления ресурсами, используемыми следующими исполняемыми объектами в экземпляре ядра СУБД.

+ Rterm. exe при вызове локально из SQL Server или удаленного вызова с SQL Server в качестве контекста удаленного вычислений
+ Python. exe при вызове локально из SQL Server или удаленного вызова с SQL Server в качестве контекста удаленного вычислений
+ BxlServer.exe и вспомогательными процессами;
+ Вспомогательные процессы, запускаемые панелью запуска, например Писонлаунчер. dll
  
> [!NOTE]
> Прямое управление службой панели запуска с помощью Resource Governor не поддерживается. Панель запуска — это доверенная служба, которая может размещать только те запуски, которые предоставляются корпорацией Майкрософт. Доверенные средства запуска настраиваются явно, чтобы избежать чрезмерного потребления ресурсов.
  
## <a name="next-steps"></a>Следующие шаги

+ [Создание пула ресурсов для машинного обучения](create-external-resource-pool.md)
+ [Пулы ресурсов Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
