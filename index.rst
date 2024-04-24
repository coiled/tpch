Benchmark Results for Dask, Spark, DuckDB, and Polars
=====================================================

This report illustrates benchmark results from unofficial Data Analytic
TPC-H benchmarks comparing Dask with Spark, DuckDB and Polars.

.. tab-set::

   .. tab-item:: Local

       .. tab-set::

          .. tab-item:: 10 GB

            .. altair-plot::
               :remove-code:

               import altair as alt
               alt.Chart.from_json(open("charts/local-10.json").read())

          .. tab-item:: 100 GB

            .. altair-plot::
               :remove-code:

               alt.Chart.from_json(open("charts/local-100.json").read())

   .. tab-item:: Cloud
      :selected:

       .. tab-set::

          .. tab-item:: 10 GB

            .. altair-plot::
               :remove-code:

               import altair as alt
               alt.Chart.from_json(open("charts/cloud-10.json").read())

          .. tab-item:: 100 GB

            .. altair-plot::
               :remove-code:

               alt.Chart.from_json(open("charts/cloud-100.json").read())

          .. tab-item:: 1 TB
            :selected:

            .. altair-plot::
               :remove-code:

               alt.Chart.from_json(open("charts/cloud-1000.json").read())

          .. tab-item:: 10 TB

            .. altair-plot::
               :remove-code:

               alt.Chart.from_json(open("charts/cloud-10000.json").read())

These charts showcase the performance of all 22 Queries on different scales for
all engines.

Methodology
-----------

We ran the TPC-H benchmarks with Dask, Spark, DuckDB and Polars on a variety of scales.
The implementation can be found in the
`Coiled Benchmarks Repository <https://github.com/coiled/benchmarks/tree/main/tests/tpch>`_.
See the `Readme <https://github.com/coiled/benchmarks/blob/main/tests/tpch/README.md>`_
for instructions on how to run the benchmarks yourself. You will need a Coiled account to
run the benchmarks as is.

Cloud
+++++

The benchmarks were run with [Coiled](https://docs.coiled.io/user_guide/index.html).
DuckDB and Polars both ran on a single, large machine with
[Coiled Functions](https://docs.coiled.io/user_guide/usage/functions/index.html).
Dask and Spark both ran on a cluster of machines that were deployed with Coiled on
AWS. All machines are from the EC2 m6i family with different configurations.

Dask uses m6i.large machines with 2 vCPUs and 8 GB of memory on scales 10 and 100 and
m6i.xlarge machines on scale 1 000 and 10 000, while Spark uses
.... We noticed that Spark performs better on bigger machines.

- **10 GB:** The engines have 16 VCPUs and 64 GB of memory available.
- **100 GB:** The engines have 32 VCPUs and 128 GB of memory available.
- **1 TB:** The engines have 128 VCPUs and 512 GB of memory available. Every machine has
  128 GB of disk space attached to it for the distributed engines.
- **10 TB - Small Configuration:** The engines have 128 VCPUs and 512 GB of memory available.
  Every machine has 200 GB of disk space attached to it for the distributed engines.
  This configuration uses the biggest m6i machine for DuckDB.
- **10 TB - Large Configuration:** The engines have 1280 VCPUs and approximately 5 TB of memory available.
  Every machine has 200 GB of disk space attached to it for the distributed engines. Only Spark and
  Dask were run on this configuration.

The data are stored on S3 and are read from there by all engines. The buckets can be found here:

- **10 GB:** `s3://coiled-runtime-ci/tpc-h/snappy/scale-10/`
- **100 GB:** `s3://coiled-runtime-ci/tpc-h/snappy/scale-100/`
- **1 TB:** `s3://coiled-runtime-ci/tpc-h/snappy/scale-1000/`
- **10 TB:** `s3://coiled-runtime-ci/tpc-h/snappy/scale-10000/`

The buckets are publicly available. The data are stored in Parquet format with Snappy compression.
We used the DuckDB data generator for the TPC-H queries and used PyArrow to write partitions
with roughly 100MB each on disk. The files are partially inhomogeneous.

Local
+++++

The benchmarks were run on a MacBook Pro with Apple Silicone CPUs. The specification is as
follows:

TODO

The environment was noisy and not clean to validate how the engines perform in a real-world
development setting. The data were stored on the local disk.
