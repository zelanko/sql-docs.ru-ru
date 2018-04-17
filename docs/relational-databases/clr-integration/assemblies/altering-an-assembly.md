---
title: Изменение сборки | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
caps.latest.revision: 14
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8de2f53e2ccbf082a057ebc35e92fe08f3c76b8e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 Набор разрешений для сборки можно также изменить с помощью инструкции ALTER ASSEMBLY. Следующая инструкция меняет набор разрешений сборки SQLCLRTest на **EXTERNAL_ACCESS**.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Если набор разрешений сборки меняется с **БЕЗОПАСНОМ** для **EXTERNAL_ACCESS** или **UNSAFE**, ассиметричный ключ и соответствующее имя входа с  **EXTERNAL ACCESS ASSEMBLY** разрешение или **UNSAFE ASSEMBLY** разрешений для сборки, необходимо создать. Дополнительные сведения см. в статье [Creating an Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Дополнение исходного кода в сборку  
 Предложение ADD FILE в синтаксисе инструкции ALTER ASSEMBLY отсутствует в инструкции CREATE ASSEMBLY. Оно обеспечивает возможность добавления исходного кода или любых других файлов, связанных со сборкой. Файлы копируются из исходных расположений и сохраняются в системных таблицах базы данных. Это обеспечивает постоянную доступность исходного кода или других файлов на тот случай, если возникнет необходимость повторного создания или документирования текущей версии определяемого пользователем типа.  
  
 Следующая инструкция добавляет исходный код класса Point.cs к сборке Point UDT. В результате этого текст, содержащийся в файле Point.cs, будет скопирован и сохранен в базе данных с именем PointSource.  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>См. также  
 [Управление сборками интеграции со средой CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [При удалении сборки](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ALTER ASSEMBLY (Transact-SQL)](../../../t-sql/statements/alter-assembly-transact-sql.md)  
  
  
