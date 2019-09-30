---
title: Пользовательские свойства назначения "Модуль чтения данных" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b2e9ebcf8464b17712d36fc43c86b7785de9ae7
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71292997"
---
# <a name="datareader-destination-custom-properties"></a>Пользовательские свойства назначения «Модуль чтения данных»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Назначение «Модуль чтения данных» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Модуль чтения данных». Все свойства, за исключением **DataReader** , доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|DataReader|String|Имя класса назначения «Модуль чтения данных».|  
|FailOnTimeout|Логическое значение|Показывает, завершать ли работу с ошибкой, когда истекает время ожидания чтения ( **ReadTimeout** ). Это свойство имеет значение по умолчанию **False**.|  
|ReadTimeout|Целочисленный|Количество миллисекунд до истечения времени ожидания. По умолчанию для этого свойства устанавливается значение 30000 (30 секунд).|  
  
 Ввод и входные столбцы назначения «Модуль чтения данных» не обладают пользовательскими свойствами.  
  
 Дополнительные сведения см. в статье [DataReader Destination](../../integration-services/data-flow/datareader-destination.md).  
  
## <a name="see-also"></a>См. также:  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
