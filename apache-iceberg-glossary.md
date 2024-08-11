# Apache Iceberg Glossary

## Catalogs
Tasks like creating, dropping, and renaming tables are the responsibility of a catalog.  Catalogs manage a collection of tables that are usually grouped into namespaces.  The most important responsibility of a catalog is tracking a table's current metadata, which is provided by the catalog when you load a table.

## Data Layer
The data layer of an Apache Iceberg table is what stores the actual data of the table and is primarily made up of the datafiles themselves, although delete files are also included.

## Metadata Layer
Apache Iceberg Metadata Layer contains [metadata files](#metadata-file), [manifest lists](#manifest-list), and [manifest files](#manifest-file).

### Manifest file
A list of datafiles, containing each datafile’s location/path and key metadata about those datafiles, which allows for creating more efficient execution plans.

### Manifest list
Files that define a single snapshot of the table as a list of manifest files along with stats on those manifests that allow for creating more efficient execution plans.

### Metadata file
Files that define a table’s structure, including its schema, partitioning scheme, and a listing of snapshots.

## Table
What consistutes an Apache Iceberg Table is its [Metadata Layer](#metadata-layer) and [Data Layer](#data-layer).
