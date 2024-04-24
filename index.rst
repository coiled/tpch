Benchmark Results for Spark, Dask, DuckDB, and Polars
=====================================================

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

Source code for all queries is available in the `coiled/benchmarks repo <https://github.com/coiled/benchmarks/tree/main/tests/tpch>`_. Watch our `YouTube video <https://www.youtube.com/watch?v=wKH0-zs2g_U>`_ for more details on why TPC-H, how we attempt to address our Dask bias, where Dask can be more efficient, and how you can run these benchmarks yourself.
