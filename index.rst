Benchmark Results
=================

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

          .. tab-item:: 1000 GB

            .. altair-plot::
               :remove-code:

               alt.Chart.from_json(open("charts/cloud-1000.json").read())

          .. tab-item:: 10 TB

            .. altair-plot::
               :remove-code:

               alt.Chart.from_json(open("charts/cloud-10000.json").read())
