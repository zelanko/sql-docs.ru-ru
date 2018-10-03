---
title: Изменение сборки | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 780b64f59143d3bf2b8ef99e3da6d32a1fe160cc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158664"
---
# <a name="altering-an-assembly"></a>Изменение сборки
  Сборку, зарегистрированную в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], можно обновить до более поздней версии при помощи инструкции ALTER ASSEMBLY. Для этого применяется следующий синтаксис инструкции ALTER ASSEMBLY.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 Инструкция ALTER ASSEMBLY не прерывает выполняемые процессы, в которых используются эта сборка, — они продолжают использовать ее прежнюю версию. Инструкция ALTER ASSEMBLY не может быть использована для изменения подписи функций среды CLR, агрегатных функций, хранимых процедур и триггеров. К сборке могут быть добавлены новые общие методы, частные методы могут быть каким угодно образом изменены, а общие могут быть изменены при условии неизменности их подписей и атрибутов. Поля в определяемом пользователем типе с собственной сериализацией, в том числе элементы данных или основные классы, нельзя изменить с помощью ALTER ASSEMBLY. Любые другие изменения не поддерживаются. Дополнительные сведения см. в разделе [ALTER ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-assembly-transact-sql).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>Изменение набора разрешений для сборки  
 Набор разрешений для сборки можно также изменить с помощью инструкции ALTER ASSEMBLY. Следующая инструкция меняет набор разрешений сборки SQLCLRTest на `EXTERNAL_ACCESS`.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Если набор разрешений сборки меняется с `SAFE` на `EXTERNAL_ACCESS` или `UNSAFE`, то необходимо вначале создать для сборки ассиметричный ключ и соответствующее имя входа с разрешением `EXTERNAL ACCESS ASSEMBLY` или `UNSAFE ASSEMBLY`. Дополнительные сведения см. в статье [Creating an Assembly](creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Дополнение исходного кода в сборку  
 Предложение ADD FILE в синтаксисе инструкции ALTER ASSEMBLY отсутствует в инструкции CREATE ASSEMBLY. Оно обеспечивает возможность добавления исходного кода или любых других файлов, связанных со сборкой. Файлы копируются из исходных расположений и сохраняются в системных таблицах базы данных. Это обеспечивает постоянную доступность исходного кода или других файлов на тот случай, если возникнет необходимость повторного создания или документирования текущей версии определяемого пользователем типа.  
  
 Следующая инструкция добавляет исходный код класса Point.cs к сборке Point UDT. В результате этого текст, содержащийся в файле Point.cs, будет скопирован и сохранен в базе данных с именем PointSource.  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>См. также  
 [Управление сборками интеграции со средой CLR](managing-clr-integration-assemblies.md)   
 [Создание сборки](creating-an-assembly.md)   
 [При удалении сборки](dropping-an-assembly.md)   
 [ALTER ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/alter-assembly-transact-sql)  
  
  
