---
title: Optimieren von parametrisierten Zeilenfiltern |Microsoft Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5e88dba53d1da9ecf2dcc3de0d69d7a2f2632eb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208490"
---
# <a name="optimize-parameterized-row-filters"></a>Optimieren von parametrisierten Zeilenfiltern
  In diesem Thema wird beschrieben, wie parametrisierte Zeilenfilter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]optimiert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
-   **So optimieren Sie parametrisierte Zeilenfilter mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Wenn Sie parametrisierte Filter verwenden, können Sie festlegen, wie die Filter durch die Mergereplikation verarbeitet werden, indem Sie bei der Erstellung der Veröffentlichung entweder die Option **use partition groups** oder die Option **keep partition changes** wählen. Diese Optionen verbessern bei Veröffentlichungen mit gefilterten Artikeln die Synchronisierungsleistung, da in der Veröffentlichungsdatenbank zusätzliche Metadaten gespeichert werden. Sie können steuern, wie die Daten auf die einzelnen Abonnenten aufgeteilt werden, indem Sie bei der Erstellung eines Artikels **partition options** festlegen. Weitere Informationen zu diesen Anforderungen finden Sie unter [Parametrisierte Zeilenfilter](../merge/parameterized-filters-parameterized-row-filters.md).  
  
     Mit [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact-Abonnenten muss "keep_partition_changes" auf "true" festgelegt werden, um sicherzustellen, dass Löschvorgänge ordnungsgemäß weitergegeben werden. Wenn die Einstellung auf "false" festgelegt ist, erhält der Abonnent möglicherweise mehr Zeilen als erwartet.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Folgende Einstellungen können zur Optimierung von parametrisierten Zeilenfiltern verwendet werden:  
  
 **Partition Options**  
 Legen Sie diese Option auf der Seite **Eigenschaften** des Dialogfelds **Artikeleigenschaften – \<Artikel>** oder über das Dialogfeld **Filter hinzufügen** fest. Der Zugriff auf beide Dialogfelder ist über den Assistenten für neue Veröffentlichung sowie über das Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** verfügbar. Im Dialogfeld **Artikeleigenschaften -.\<Artikel>**, können Sie weitere Werte für diese Option angeben, die im Dialogfeld **Filter hinzufügen** nicht verfügbar sind.  
  
 **Partitionen im Voraus berechnen**  
 Diese Option ist standardmäßig auf **Wahr** festgelegt, wenn die Artikel in Ihrer Veröffentlichung einem Satz von Anforderungen entsprechen. Weitere Informationen zu diesen Anforderungen finden Sie unter [Parametrisierte Filter-Leistung mit Vorausberechneten Partitionen optimieren](../merge/parameterized-filters-optimize-for-precomputed-partitions.md). Diese Option können Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** ändern.  
  
 **Synchronisierung optimieren**  
 Diese Option sollte nur auf **Wahr** festgelegt werden, wenn **Partitionen im Voraus berechnen** auf **Falsch**festgelegt ist. Diese Option können Sie auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften - \<Veröffentlichung>** festlegen.  
  
 Weitere Informationen zum Assistenten für neue Veröffentlichung sowie zum Zugriff auf das Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** finden Sie unter [Eine Veröffentlichung erstellen](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a>So legen Sie Partitionsoptionen im Dialogfeld Filter hinzufügen bzw. Filter bearbeiten fest  
  
1.  Klicken Sie auf der Seite **Tabellenzeilen filtern** im Assistenten für neue Veröffentlichung bzw. auf der Seite **Zeilen filtern** im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** zunächst auf **Hinzufügen** und anschließend auf **Filter hinzufügen**.  
  
2.  Erstellen Sie einen parametrisierten Filter. Weitere Informationen finden Sie unter [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
3.  Wählen Sie die Option aus, mit der angegeben wird, wie Daten für mehrere Abonnenten freigegeben werden:  
  
    -   **Eine Zeile aus dieser Tabelle wird an mehrere Abonnements gesendet**  
  
    -   **Eine Zeile aus dieser Tabelle wird nur an ein Abonnement gesendet**  
  
     Wenn Sie **Eine Zeile aus dieser Tabelle wird nur an ein Abonnement gesendet**auswählen, kann die Mergereplikation die Leistung optimieren, da weniger Metadaten gespeichert und verarbeitet werden. Sie müssen jedoch sicherstellen, dass die Daten so partitioniert werden, dass eine Zeile nicht für mehrere Abonnenten repliziert werden kann. Weitere Informationen finden Sie im Abschnitt zum Festlegen von Partitionsoptionen unter [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften.-.\<Veröffentlichung>** befinden, klicken Sie auf **OK**, um zu speichern und das Dialogfeld zu schließen.  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a>So legen Sie Partitionsoptionen im Dialogfeld Artikeleigenschaften - \<Artikel> fest  
  
1.  Wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Artikel** bzw. im Dialogfeld **Veröffentlichungseigenschaften – \<Veröffentlichung>** eine Tabelle aus, und klicken anschließend auf **Artikeleigenschaften**.  
  
2.  Klicken Sie auf **Eigenschaften des hervorgehobenen Tabelle-Artikels festlegen** oder **Eigenschaften aller Tabellenartikel festlegen**.  
  
3.  Geben Sie im Abschnitt **Zielobjekt** der Registerkarte **Eigenschaften** des Dialogfensters **Artikeleigenschaften - \<Artikel>** einen der folgenden Werte für **Partitionsoptionen** an:  
  
    -   **Überlappend**  
  
    -   **Überlappend, Datenänderungen außerhalb der Partition nicht zulassen**  
  
    -   **Nicht überlappend, ein Abonnement**  
  
    -   **Nicht überlappend, für mehrere Abonnements freigegeben**  
  
     Weitere Informationen zu diesen Optionen und dazu, in welcher Beziehung Sie zu den Optionen stehen, die im Dialogfeld **Filter hinzufügen** und **Filter bearbeiten** verfügbar sind, finden Sie im Abschnitt über das Festlegen von Partitionsoptionen unter [Parametrisierte Zeilenfilter](../merge/parameterized-filters-parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Wenn Sie sich im Dialogfeld **Veröffentlichungseigenschaften.-.\<Veröffentlichung>** befinden, klicken Sie auf **OK**, um zu speichern und das Dialogfeld zu schließen.  
  
#### <a name="to-set-precompute-partitions"></a>So legen Sie einen Wert für Partitionen im Voraus berechnen fest  
  
1.  Wählen Sie auf der Seite **Abonnementoptionen** im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** einen Wert für die Option **Partitionen im Voraus berechnen** aus. Die Eigenschaft ist in folgenden Fällen schreibgeschützt:  
  
    -   Die Veröffentlichung erfüllt die Anforderungen für im Voraus berechnete Partitionen nicht.  
  
    -   Es wurde noch keine Momentaufnahme für die Veröffentlichung generiert. In diesem Fall wird für die Option der Wert **Wird automatisch beim Erstellen einer Momentaufnahme festgelegt**angezeigt.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a>So legen Sie einen Wert für Synchronisierung optimieren fest  
  
1.  Wählen Sie auf der Seite **Abonnementoptionen** im Dialogfeld **Veröffentlichungseigenschaften - \<Veröffentlichung>** einen Wert für **Wahr** für die Option **Synchronisierung optimieren** aus.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Informationen zur Definition der Filteroptionen für **@keep_partition_changes** und **@use_partition_groups**finden Sie unter [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)optimiert werden.  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a>So geben Sie die Optimierungen für Mergefilter beim Erstellen einer neuen Veröffentlichung an  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)aus. Geben Sie **@publication** und den Wert `true` für eine der folgenden Parameter:  
  
    -   **@use_partition_groups**: &ndash; die höchste Leistungsoptimierung, vorausgesetzt, dass die Artikel den Anforderungen für vorausberechnete Partitionen entsprechen. Weitere Informationen finden Sie unter [parametrisierte Filter-Leistung mit Vorausberechneten Partitionen optimieren](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
    -   **@keep_partition_changes** &ndash; verwenden Sie diese Optimierung, wenn vorausberechnete Partitionen nicht verwendet werden können.  
  
2.  Fügen Sie einen Momentaufnahme-Auftrag für die Veröffentlichung hinzu. Weitere Informationen finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md).  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)aus, und geben Sie die folgenden Parameter an:  
  
    -   **@publication** &ndash; der Name der Veröffentlichung aus Schritt 1.  
  
    -   **@article** &ndash; ein Name für den Artikel.  
  
    -   **@source_object** &ndash; das Datenbankobjekt, das veröffentlicht wird.  
  
    -   **@subset_filterclause** &ndash; die optionale parametrisierte Filterklausel, die verwendet wird, um den Artikel horizontal zu filtern.  
  
    -   **@partition_options** &ndash; die Partitionsoptionen für den gefilterten Artikel.  
  
4.  Wiederholen Sie Schritt 3 für jeden Artikel in der Veröffentlichung.  
  
5.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) aus, um einen Joinfilter zwischen zwei Artikeln zu definieren. Weitere Informationen finden Sie unter [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a>So zeigen Sie das Verhalten von Mergefiltern für eine vorhandene Veröffentlichung an und ändern es  
  
1.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)unter Angabe von **@publication**optimiert werden. Achten Sie auf den Wert von **keep_partition_changes** und **use_partition_groups** im Resultset.  
  
2.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus. Geben Sie den Wert **Use_partition_groups** für **@property** und entweder `true` oder `false` für **@value**.  
  
3.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)aus. Geben Sie den Wert **Keep_partition_changes** für **@property** und entweder `true` oder `false` für **@value**.  
  
    > [!NOTE]  
    >  Wenn Sie **keep_partition_changes**aktivieren, müssen Sie zuerst **use_partition_groups** deaktivieren und den Wert **1** für **@force_reinit_subscription**optimiert werden.  
  
4.  (Optional) Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus. Geben Sie den Wert **partition_options** für **@property** und den entsprechenden Wert für **@value**optimiert werden. Informationen zur Definition dieser Filteroptionen finden Sie unter [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) .  
  
5.  (Optional) Starten Sie den Momentaufnahme-Agent, um, wenn notwendig, die Momentaufnahme erneut zu generieren. Informationen dazu, welche Änderungen die Generierung einer neuen Momentaufnahme erforderlich machen, finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](change-publication-and-article-properties.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisches Generieren einer Reihe von Joinfiltern zwischen Mergeartikeln &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md)   
 [Definieren und ändern Sie einen parametrisierten Zeilenfilter mit Mergeartikeln](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
