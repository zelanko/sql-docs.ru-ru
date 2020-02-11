---
title: Изменение сборки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: 80ef9d283f90c50406477a7a651fb418694ae445
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68027947"
---
# <a name="altering-an-assembly"></a>Изменение сборки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Сборку, зарегистрированную в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], можно обновить до более поздней версии при помощи инструкции ALTER ASSEMBLY. Для этого применяется следующий синтаксис инструкции ALTER ASSEMBLY.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 Инструкция ALTER ASSEMBLY не прерывает выполняемые процессы, в которых используются эта сборка, — они продолжают использовать ее прежнюю версию. Инструкция ALTER ASSEMBLY не может быть использована для изменения подписи функций среды CLR, агрегатных функций, хранимых процедур и триггеров. К сборке могут быть добавлены новые общие методы, частные методы могут быть каким угодно образом изменены, а общие могут быть изменены при условии неизменности их подписей и атрибутов. Поля в определяемом пользователем типе с собственной сериализацией, в том числе элементы данных или основные классы, нельзя изменить с помощью ALTER ASSEMBLY. Любые другие изменения не поддерживаются. Дополнительные сведения см. в разделе [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>Изменение набора разрешений для сборки  
 Набор разрешений для сборки можно также изменить с помощью инструкции ALTER ASSEMBLY. Следующая инструкция изменяет набор разрешений сборки Склклртест на **EXTERNAL_ACCESS**.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Если набор разрешений сборки изменяется с **безопасного** на **EXTERNAL_ACCESS** или **незащищенный**, необходимо сначала создать асимметричный ключ и СООТВЕТСТВУЮЩЕЕ разрешение на сборку **доступа к сборке** или на **ненадежное сборку** . Дополнительные сведения см. в статье [Creating an Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Дополнение исходного кода в сборку  
 Предложение ADD FILE в синтаксисе инструкции ALTER ASSEMBLY отсутствует в инструкции CREATE ASSEMBLY. Оно обеспечивает возможность добавления исходного кода или любых других файлов, связанных со сборкой. Файлы копируются из исходных расположений и сохраняются в системных таблицах базы данных. Это обеспечивает постоянную доступность исходного кода или других файлов на тот случай, если возникнет необходимость повторного создания или документирования текущей версии определяемого пользователем типа.  
  
 Следующая инструкция добавляет исходный код класса Point.cs к сборке Point UDT. В результате этого текст, содержащийся в файле Point.cs, будет скопирован и сохранен в базе данных с именем PointSource.  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками интеграции со средой CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Удаление сборки](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ALTER ASSEMBLY &#40;&#41;Transact-SQL](../../../t-sql/statements/alter-assembly-transact-sql.md)  
  
  
