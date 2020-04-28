---
title: Задача 16. Проверка с помощью диспетчер основных данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d9828c02625ae2bc5a85859577a237b4c4fa99c5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81484684"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Задача 16. Проверка с помощью диспетчера основных данных
  В этой задаче вы проверите состояние пакетного задания, отправленного пакетом служб SSIS, и убедитесь, что данные были переданы на сервер MDS с помощью диспетчера основных данных.  
  
1.  Запуск **Диспетчер основных данных** (`http://localhost/MDS`). Если она уже открыта, щелкните **Microsoft SQL Server Master Data Services** в верхней части, чтобы перейти на **домашнюю страницу**.  
  
2.  Щелкните **Управление интеграцией**.  
  
3.  Обратите внимание, что существует пакет с именем **еимбатч** , отправленный в списке. Щелкните **Импорт данных** в строке меню, если не отображается следующий экран.  
  
     ![Пакет EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "Пакет EIM")  
  
4.  Вернитесь на домашнюю страницу, щелкнув **SQL Server 2012 Master Data Services** в верхней части страницы.  
  
5.  Убедитесь, что для **model** выбрана модель **поставщики** и **VERSION_1** выбрана **версия**, и нажмите кнопку **Обозреватель**.  
  
6.  Вы можете просмотреть данные, импортированные пакетом служб SSIS в MDS. Данные должны быть очищены и не иметь повторяющихся значений **кода** (Примечание: столбец « **КодПоставщика** » в Excel соответствует атрибуту **Code** сущности «поставщик» в MDS).  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 17. Проверка проекта очистки DQS, созданного пакетом SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
