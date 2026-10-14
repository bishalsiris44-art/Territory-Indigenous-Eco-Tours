Territory Indigenous & Eco Tours — Task 2 Neo4j Migration Package
=================================================================

SOURCE
------
Generated directly from Relations_4Scripts(1).sql.

CONTENTS
--------
csv/        26 CSV files exported from the relational tables
import.txt  Complete Cypher migration + constraints/indexes + verification
territory_tours_source.sqlite  Temporary SQLite reconstruction used to export the CSVs

EXPECTED GRAPH AFTER IMPORT
---------------------------
Core nodes: 41
Relationships: 42

Expected core node counts:
Tourist                 4
Booking                 7
Review                  4
TourOperation           5
TourPackage             4
Vehicle                 3
TourGuide               3
Activity                4
TourSite                4
IndigenousCommunity     3

Expected relationship counts:
MAKES                   7
BOOKS                   7
HAS_REVIEW              4
FOR_PACKAGE             5
USES                    5
GUIDED_BY               6
VISITS                  5
INCLUDES                6
SUPPORTED_BY            2

SPECIALISATION LABELS
---------------------
EcoTour                 3
IndigenousTour          2
IndigenousGuide         2
EcoGuide                2
IndigenousActivity      2
EcoActivity             2
CulturalSite            2
EcoSite                 2

NOTES
-----
- Relational subtype rows become additional Neo4j labels/properties.
- Relational multivalued phone/email tables become list properties.
- Foreign keys become graph relationships rather than duplicate FK properties.
- package_activity.seq_no becomes a property on the INCLUDES relationship.
- indigenous_tour.community_id creates SUPPORTED_BY only from IndigenousTour packages.
