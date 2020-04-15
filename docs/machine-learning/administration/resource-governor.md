---
title: Управление с помощью Resource Governor
description: Узнайте, как использовать Resource Governor для управления ресурсами ЦП, физическими операциями ввода-вывода и выделением ресурсов памяти для рабочих нагрузок Python и R в службах машинного обучения SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/02/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 85556d545bd0ae9760f2adc92ef5a63c9a502a76
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2020
ms.locfileid: "81118817"
---
# <a name="manage-python-and-r-workloads-with-resource-governor-in-sql-server-machine-learning-services"></a>Управление рабочими нагрузками Python и R с помощью Resource Governor в службах машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Узнайте, как использовать [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) для управления ресурсами ЦП, физическими операциями ввода-вывода и выделением ресурсов памяти для рабочих нагрузок Python и R в службах машинного обучения SQL Server.

Алгоритмы машинного обучения в Python и R обычно являются ресурсоемкими. В зависимости от приоритетов рабочих нагрузок может потребоваться увеличить или уменьшить объем доступных ресурсов для служб машинного обучения.

Дополнительные сведения см. в разделе [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).

> [!NOTE] 
> Resource Governor доступен в составе выпуска Enterprise.

## <a name="default-allocations"></a>Выделения по умолчанию

По умолчанию объем памяти, выделяемый для внешних сред выполнения сценариев машинного обучения, ограничен 20% от общего объема памяти компьютера. Иногда это зависит от системы, но в общем случае это ограничение не подходит для серьезных задач машинного обучения, таких как обучение моделей или прогнозирование на основе большого числа строк данных. 

## <a name="manage-resources-with-resource-governor"></a>Управление ресурсами с помощью Resource Governor
 
По умолчанию внешние процессы используют до 20% общего объема памяти узла на локальном сервере. Пул ресурсов по умолчанию можно изменить, чтобы внести изменения на уровне сервера, а процессы R и Python будут использовать любую емкость, доступную для внешних процессов.

Кроме того, можно создать настраиваемые **внешние пулы ресурсов** со связанными группами рабочих нагрузок и классификаторами, чтобы определить выделение ресурсов для запросов, исходящих от конкретных программ или узлов, или в соответствии с другими указанными условиями. Внешний пул ресурсов — это тип пула ресурсов в [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], который помогает управлять процессами R и Python за пределами ядра СУБД.

1. [Включите управление ресурсами](https://docs.microsoft.com/sql/relational-databases/resource-governor/enable-resource-governor) (по умолчанию оно отключено).

2. Выполните инструкцию [CREATE EXTERNAL RESOURCE POOL](https://docs.microsoft.com/sql/t-sql/statements/create-external-resource-pool-transact-sql), чтобы создать и настроить пул ресурсов, а затем инструкцию [ALTER RESOURCE GOVERNOR](https://docs.microsoft.com/sql/t-sql/statements/alter-resource-governor-transact-sql), чтобы реализовать его.

3. Создайте группу рабочей нагрузки для детализированного выделения, например, между обработкой и оценкой.

4. Создайте классификатор для перехвата вызовов для внешней обработки.

5. Выполняйте запросы и процедуры с помощью созданных объектов.

Пошаговые инструкции см. в статье [Создание пула ресурсов для Служб машинного обучения SQL Server](create-external-resource-pool.md).

Общие сведения о терминологии и основных понятиях см. в разделе [Пул ресурсов Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

## <a name="processes-under-resource-governance"></a>Процессы, для которых применяется управление ресурсами
  
 С помощью *внешнего пула ресурсов* вы можете управлять ресурсами, используемыми следующими исполняемыми файлами в экземпляре ядра СУБД:

+ Rterm.exe при вызове локально из SQL Server или при удаленном вызове из SQL Server в качестве удаленного контекста вычислений;
+ Python.exe при вызове локально из SQL Server или при удаленном вызове из SQL Server в качестве удаленного контекста вычислений;
+ BxlServer.exe и вспомогательными процессами;
+ вспомогательными процессами, запущенными с помощью панели запуска, например, PythonLauncher.dll;
  
> [!NOTE]
> Прямое управление службой панели запуска с помощью Resource Governor не поддерживается. Панель запуска — это доверенная служба, которая может размещать только те запуски, которые предоставляются корпорацией Майкрософт. Доверенные средства запуска настраиваются явным образом, чтобы избежать чрезмерного использования ресурсов.
  
## <a name="next-steps"></a>Дальнейшие действия

+ [Создание пула ресурсов для машинного обучения](create-external-resource-pool.md)
+ [Пулы ресурсов Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
