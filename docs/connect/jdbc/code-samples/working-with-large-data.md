---
title: Работа с большим объемом данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9163e9244b46e4eeb26cb0766186d7bfdb38fbf1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-large-data"></a>Работа с большими объемами данных
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Драйвер JDBC реализует поддержку адаптивной буферизации, которая позволяет получать любые данные большого объема, не расходуя ресурсы на серверные курсоры. При адаптивной буферизации [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] извлекает результаты выполнения инструкции из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] как приложение должно их, а не все сразу. Драйвер также удаляет результаты, когда приложение теряет к ним доступ.  
  
 В [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)] драйвера JDBC версии 1.2, использовался режим буферизации «**полного**» по умолчанию. Если приложение не задано свойство соединения «responseBuffering» значение «**адаптивной**» в свойствах соединения или с помощью [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метод [ SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объект, то драйвер поддерживал одновременное считывание всех результатов с сервера. Чтобы получить режим адаптивной буферизации, приложение должно было устанавливать свойство соединения «responseBuffering» «**адаптивный**» явным образом.  
  
 **Адаптивной** значение — режим буферизации по умолчанию и драйвер JDBC выполняет буферизацию минимума данных при необходимости. Дополнительные сведения об использовании адаптивной буферизации см. в разделе [с помощью адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 В подразделах этого раздела описываются различные способы можно использовать для получения данных большого объема из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Пример считывания данных большого объема](../../../connect/jdbc/reading-large-data-sample.md)|Описывает получение данных большого объема с помощью инструкции SQL.|  
|[Пример считывания данных большого объема с помощью хранимых процедур](../../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md)|Описывает получение значений параметра CallableStatement OUT большого объема.|  
|[Пример обновления данных большого объема](../../../connect/jdbc/updating-large-data-sample.md)|Описывает обновление данных большого объема в базе данных.|  
  
## <a name="see-also"></a>См. также  
 [Пример приложений драйвера JDBC](../../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
