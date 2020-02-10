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
ms.openlocfilehash: 35dd2da7f6cf6598918cd9d109b97f3d314556d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484690"
---
# <a name="task-16-verifying-with-master-data-manager"></a>Задача 16. Проверка с помощью диспетчера основных данных
  В этой задаче вы проверите состояние пакетного задания, отправленного пакетом служб SSIS, и убедитесь, что данные были переданы на сервер MDS с помощью диспетчера основных данных.  
  
1.  Запуск **Диспетчер основных данных** ([http://localhost/MDS](http://localhost/MDS)). Если она уже открыта, щелкните **Microsoft SQL Server Master Data Services** в верхней части, чтобы перейти на **домашнюю страницу**.  
  
2.  Щелкните **Управление интеграцией**.  
  
3.  Обратите внимание, что существует пакет с именем **еимбатч** , отправленный в списке. Щелкните **Импорт данных** в строке меню, если не отображается следующий экран.  
  
     ![Пакет EIM](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "Пакет EIM")  
  
4.  Вернитесь на домашнюю страницу, щелкнув **SQL Server 2012 Master Data Services** в верхней части страницы.  
  
5.  Убедитесь, что для **model** выбрана модель **поставщики** и **VERSION_1** выбрана **версия**, и нажмите кнопку **Обозреватель**.  
  
6.  Вы можете просмотреть данные, импортированные пакетом служб SSIS в MDS. Данные должны быть очищены и не иметь повторяющихся значений **кода** (Примечание: столбец « **КодПоставщика** » в Excel соответствует атрибуту **Code** сущности «поставщик» в MDS).  
  
## <a name="next-step"></a>Дальнейшее действие  
 [Задача 17. Обзор проекта очистки данных DQS, созданного пакетом служб SSIS](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
