---
title: Aktiviert-Eigenschaft (ServerNetworkProtocolIpAddress-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- Enabled Property (ServerNetworkProtocolIpAddress Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Enabled property
ms.assetid: 870fd4d0-6c77-462a-b480-d42eb044b2e7
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cf25d25a4d187d31f602cb79f4c0df74a0340e88
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730038"
---
# <a name="enabled-property-servernetworkprotocolipaddress-class"></a>Enabled-Eigenschaft (ServerNetworkProtocolIpAddress-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft die boolesche Eigenschaft ab, die angibt, ob eine IP-Adresse aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Enabled [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 A [ServerNetworkProtocolIPAdress-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) , das eine IP-Adresse für das Netzwerkprotokoll in der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boleescher Wert, der angibt, ob die IP-Adresse aktiviert ist: **true** , wenn die IP-Adresse aktiviert ist, bzw. **false** , wenn die IP-Adresse deaktiviert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
