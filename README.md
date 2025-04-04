The Auto Arborist Dataset, [published at CVPR 2022](https://openaccess.thecvf.com/content/CVPR2022/html/Beery_The_Auto_Arborist_Dataset_A_Large-Scale_Benchmark_for_Multiview_Urban_CVPR_2022_paper.html).

Usage of this dataset is subject to terms. See the [dataset webpage](https://google.github.io/auto-arborist/) for more info.

== Contents ==

The dataset consists of CSVs containing ~4.5M basic processed tree records from
23 cities and tfrecords that contain imagery for a subset of the trees.

```
README - Info about the dataset.

tree_locations/ - Contains the parsed and cleaned up tree inventories of each
  city in the dataset, along with train/test splits per city. The CSVs
  have the following columns:
  - IDX: An identifier for the row which is unique to the city.
  - SHAPE_LNG: The longitude of the tree.
  - SHAPE_LAT: The latitude of the tree.
  - GENUS: The lowercase genus of the tree.
  - TAXONOMY_ID: A unique integer ID corresponding to the genus. Note that this
      is indexed from 0.

tfrecords/ - Contains train/test TFRecord files with one aerial and blurred
  street level image per available tree for all cities available in this release
  version. The trees are a subset of the trees in tree_locations/.
  The tfrecords have the following layout:
  tree/
    id: bytes. An ID for the tree that is unique across the release dataset.
    tree_locations_idx: bytes. An ID which links to the tree_locations/ CSV IDX
                      for the tree.
    city: bytes. The city where the tree is located.
    latitude: float. The ground truth latitude of the tree.
    longitude: float. The ground truth longitude of the tree.
    genus/
      label: int64. Holds the ground truth label number representing the tree’s
             genus.
      genus: bytes. The ground truth genus of the tree.
  image/
    aerial/
      encoded: bytes. An encoded aerial JPEG image of the tree approximately
               centered on its trunk.
    streetlevel/
      encoded: bytes. An encoded street level JPEG image of the tree.
               Non-vegetation pixels are blurred.
      capturetime: bytes. The month and year that the street level image was captured.
      bbox/: float_lists. Represent tree detection bounding boxes (based on Open
              Images) as regions scaled from [0, 1], with  (0,0) representing
              the top-left corner of the image.
        xmin
        xmax
        ymin
        ymax
      center/:
        x: int64. Represents an approximate (but noisy) location for the horizontal
           center pixel of the tree in the image.
        y: int64. This is always set to half of the image height. It is provided
           for convenience.
```

== Citations ==

If you use the Auto Arborist dataset for a research publication, please consider citing:

"The Auto Arborist Dataset: A Large-Scale Benchmark for Multiview Urban Forest Monitoring Under Domain Shift." Sara Beery, Guanhang Wu, Trevor Edwards, Filip Pavetic, Bo Majewski, Shreyasee Mukherjee, Stanley Chan, John Morgan, Vivek Rathod, Jonathan Huang, CVPR 2022

Alternatively, you may provide this BibTeX citation:
```
@inproceedings{beery2022autoarborist,
  title={The Auto Arborist Dataset: A Large-Scale Benchmark for Multiview Urban Forest Monitoring Under Domain Shift.},
  author={Sara Beery and Guanhang Wu and Trevor Edwards and Filip Pavetic and Bo Majewski and Shreyasee Mukherjee and Stanley Chan and John Morgan and Vivek Rathod and Jonathan Huang},
  booktitle={CVPR},
  year={2022}
}
```
== Updates and Feedback ==

We may post updates about the project and dataset on our Google Group:
https://groups.google.com/g/auto-arborist

We would love to hear back from you if you have questions or suggestions or
success stories relating to this dataset. You can reach out to us at:
auto-arborist-external@google.com.

We have used a combination of automatic and manual methods to blur out
non-vegetation pixels in our dataset in order to protect privacy.  However, if
you find any private or otherwise objectionable content, please contact us at the
email above so that we may remove it.

== Attributions ==

We are thankful to the following cities for making their data available:

Bloomington, Indiana, USA
https://data.bloomington.in.gov/dataset/public-tree-inventory

Boulder, Colorado, USA
https://open-data.bouldercolorado.gov/datasets/dbbae8bdb0a44d17934243b88e85ef2b

Buffalo, New York, USA
https://data.buffalony.gov/Quality-of-Life/Tree-Inventory/n4ni-uuec/data

Calgary, Alberta, Canada
https://maps.calgary.ca/TreeSchedule/
Contains information licensed under the Open Government Licence – City of Calgary.
See license: https://data.calgary.ca/stories/s/Open-Calgary-Terms-of-Use/u45n-7awa

Cambridge, Ontario, Canada
https://data.waterloo.ca/datasets/cityofcambridge::street-trees
Contains information licensed under the Open Government Licence – City of Cambridge.
See license: https://maps.cambridge.ca/images/opendata/Open%20data%20licence.pdf

Charlottesville, Virginia, USA
https://hub.arcgis.com/datasets/charlottesville::tree-inventory-point
Credit to the City of Charlottesville. Derived data in this release is modified
from the original version.
See license: https://creativecommons.org/licenses/by/4.0/legalcode

Columbus, Ohio, USA
https://opendata.columbus.gov/datasets/public-owned-trees

Cupertino, California, USA
https://gis-cupertino.opendata.arcgis.com/datasets/Cupertino::trees

Denver, Colorado, USA
https://www.denvergov.org/opendata/dataset/city-and-county-of-denver-tree-inventory
Credit to City of Denver Open Data Catalog. Under the license terms CC BY 3.0.
See data.denvergov.org and www.creativecommons.org for more info.

Edmonton, Alberta, Canada
https://data.edmonton.ca/Environmental-Services/Trees-Map/udbt-eiax
See license: https://data.edmonton.ca/stories/s/City-of-Edmonton-Open-Data-Terms-of-Use/msh8-if28/

Kitchener, Ontario, Canada
https://data.waterloo.ca/datasets/KitchenerGIS::tree-inventory/about
Contains information licensed under the Open Government Licence - The Corporation of the City of Kitchener.

Los Angeles, California, USA
https://geohub.lacity.org/datasets/266c6255b1fc4ae8b8f100d8696e1fa4_0

Montreal, Quebec, Canada
https://donnees.montreal.ca/ville-de-montreal/arbres
Derived data in this release is modified from the original version.
See license: https://donnees.montreal.ca/licence-d-utilisation

New York, New York, USA
https://data.cityofnewyork.us/Environment/2015-Street-Tree-Census-Tree-Data/pi5s-9p35

Pittsburgh, Pennsylvania, USA
https://data.wprdc.org/dataset/city-trees
Credit to the City of Pittsburgh. Derived data in this release is modified
from the original version.
See license: https://creativecommons.org/licenses/by/4.0/legalcode

San Francisco, California, USA
https://data.sfgov.org/City-Infrastructure/Street-Tree-List/tkzw-k3nq

San Jose, California, USA
https://gisdata-csj.opendata.arcgis.com/datasets/7db16e012fe8402db45074cd260c8f4e_510

Santa Monica, California, USA
https://data.smgov.net/Public-Assets/Trees-Inventory/w8ue-6cnd
Contains information from Santa Monica Open Data which is made available
under the ODC Attribution License - https://opendatacommons.org/licenses/by/1-0/.

Seattle, Washington, USA
https://data-seattlecitygis.opendata.arcgis.com/datasets/0b8c124ace214943ab0379623937eccb_6

Sioux Falls, South Dakota, USA
https://hub.arcgis.com/datasets/cityofsfgis::trees
Credit to the City of Sioux Falls. Derived data in this release is modified
from the original version.
See license: https://creativecommons.org/licenses/by/4.0/legalcode

Surrey, British Columbia, Canada
https://data.surrey.ca/dataset/park-specimen-trees
Contains information licensed under the Open Government License – City of Surrey.
See license: https://data.surrey.ca/pages/open-government-licence-surrey

Vancouver, British Columbia, Canada
https://opendata.vancouver.ca/explore/dataset/street-trees/information
Contains information licensed under the Open Government Licence – Vancouver.
See license: https://opendata.vancouver.ca/pages/licence/

Washington DC, USA
https://opendata.dc.gov/datasets/urban-forestry-street-trees/explore
Credit to the City of Washington, DC. Derived data in this release is modified
from the original version.
See license: https://creativecommons.org/licenses/by/4.0/legalcode

Additionally, we are thankful for the Open Images Dataset which was used to help
produce tree detection bounding boxes.
https://storage.googleapis.com/openimages/web/index.html
