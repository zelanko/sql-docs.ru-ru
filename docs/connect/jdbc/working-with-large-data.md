---
title: Работа с большими объемами данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a60bc049b02ca998119fd4741fa51589a029aeca
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39452298"
---
# <a name="working-with-large-data"></a>Работа с большими объемами данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер JDBC реализует поддержку адаптивной буферизации, которая позволяет получать любые данные большого объема, не расходуя ресурсы на серверные курсоры. При адаптивной буферизации драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] получает результаты выполнения инструкции из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] по мере того, как их запрашивает приложение, а не все сразу. Драйвер также удаляет результаты, когда приложение теряет к ним доступ.

В версии [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] JDBC Driver 1.2 по умолчанию использовался режим **полной** буферизации. Если приложение не устанавливало для свойства responseBuffering значение **adaptive** в свойствах подключения или с помощью метода [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) объекта [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), то драйвер поддерживал одновременное считывание всех результатов с сервера. Чтобы включить режим адаптивной буферизации, приложение должно было явно установить для свойства подключения responseBuffering значение **adaptive**.  
  
Значение **adaptive** включает режим буферизации по умолчанию, когда драйвер JDBC выполняет буферизацию для минимально необходимого объема данных. Дополнительные сведения об использовании адаптивной буферизации см. в разделе [Using Adaptive Buffering](../../connect/jdbc/using-adaptive-buffering.md).  
  
 Здесь представлены разделы, в которых описаны различные способы получения данных большого объема из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
| Раздел                                                                                                                      | Описание                                                              |
| -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [Пример считывания данных большого объема](../../connect/jdbc/reading-large-data-sample.md)                                               | Описывает получение данных большого объема с помощью инструкции SQL.       |
| [Пример считывания данных большого объема с помощью хранимых процедур](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md) | Описывает получение значений параметра CallableStatement OUT большого объема. |
| [Пример обновления данных большого объема](../../connect/jdbc/updating-large-data-sample.md)                                             | Описывает обновление данных большого объема в базе данных.                |
  
## <a name="see-also"></a>См. также:

[Пример приложений драйвера JDBC](../../connect/jdbc/sample-jdbc-driver-applications.md)  
