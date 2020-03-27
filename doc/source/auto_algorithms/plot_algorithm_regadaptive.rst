.. note::
    :class: sphx-glr-download-link-note

    Click :ref:`here <sphx_glr_download_auto_algorithms_plot_algorithm_regadaptive.py>` to download the full example code
.. rst-class:: sphx-glr-example-title

.. _sphx_glr_auto_algorithms_plot_algorithm_regadaptive.py:


Algorithm: RegAdaptive
======================


.. code-block:: default

    import pygpc
    import numpy as np
    from collections import OrderedDict

    fn_results = 'tmp/regadaptive'   # filename of output
    save_session_format = ".hdf5"    # file format of saved gpc session ".hdf5" (slow) or ".pkl" (fast)








Loading the model and defining the problem
------------------------------------------


.. code-block:: default


    # define model
    model = pygpc.testfunctions.Ishigami()

    # define problem
    parameters = OrderedDict()
    parameters["x1"] = pygpc.Beta(pdf_shape=[1, 1], pdf_limits=[-np.pi, np.pi])
    parameters["x2"] = pygpc.Beta(pdf_shape=[1, 1], pdf_limits=[-np.pi, np.pi])
    parameters["x3"] = 0.
    parameters["a"] = 7.
    parameters["b"] = 0.1

    problem = pygpc.Problem(model, parameters)








Setting up the algorithm
------------------------


.. code-block:: default


    # gPC options
    options = dict()
    options["order_start"] = 5
    options["order_end"] = 20
    options["solver"] = "LarsLasso"
    options["interaction_order"] = 2
    options["order_max_norm"] = 0.7
    options["n_cpu"] = 0
    options["adaptive_sampling"] = True
    options["gradient_enhanced"] = True
    options["gradient_calculation"] = "FD_fwd"
    options["gradient_calculation_options"] = {"dx": 0.001, "distance_weight": -2}
    options["fn_results"] = fn_results
    options["save_session_format"] = save_session_format
    options["eps"] = 0.0075
    options["grid"] = pygpc.Random
    options["grid_options"] = None

    # define algorithm
    algorithm = pygpc.RegAdaptive(problem=problem, options=options)








Running the gpc
---------------


.. code-block:: default


    # Initialize gPC Session
    session = pygpc.Session(algorithm=algorithm)

    # run gPC algorithm
    session, coeffs, results = session.run()





.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none

    Initializing gPC object...
    Initializing gPC matrix...
    Order/Interaction order: 5/2
    ============================
    Starting adaptive sampling:
    Extending grid from 14 to 14 by 0 sampling points
    Performing simulations 1 to 14

    Total parallel function evaluation: 0.009347677230834961 sec

    Gradient evaluation: 0.0005791187286376953 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...














    LOOCV computation time: 0.07821393013000488 sec
    -> relative loocv error = 6.346391583734324
    Extending grid from 14 to 15 by 1 sampling points
    Performing simulations 15 to 15

    Total parallel function evaluation: 0.002409696578979492 sec

    Gradient evaluation: 0.0006697177886962891 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...















    LOOCV computation time: 0.11508679389953613 sec
    -> relative loocv error = 24.546614303594165
    Extending grid from 15 to 16 by 1 sampling points
    Performing simulations 16 to 16

    Total parallel function evaluation: 0.0025353431701660156 sec

    Gradient evaluation: 0.0006875991821289062 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...
















    LOOCV computation time: 0.09920573234558105 sec
    -> relative loocv error = 21.645434447819717
    Extending grid from 16 to 17 by 1 sampling points
    Performing simulations 17 to 17

    Total parallel function evaluation: 0.0025315284729003906 sec

    Gradient evaluation: 0.0006327629089355469 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

















    LOOCV computation time: 0.07691359519958496 sec
    -> relative loocv error = 5.092349121271938
    Extending grid from 17 to 18 by 1 sampling points
    Performing simulations 18 to 18

    Total parallel function evaluation: 0.002673625946044922 sec

    Gradient evaluation: 0.0007059574127197266 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...


















    LOOCV computation time: 0.07849693298339844 sec
    -> relative loocv error = 5.579273264602323
    Order/Interaction order: 6/1
    ============================
    Starting adaptive sampling:
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...


















    LOOCV computation time: 0.09241461753845215 sec
    -> relative loocv error = 0.4680176315553291
    Order/Interaction order: 6/2
    ============================
    Starting adaptive sampling:
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...


















    LOOCV computation time: 0.09682774543762207 sec
    -> relative loocv error = 0.4680176315553291
    Extending grid from 18 to 19 by 1 sampling points
    Performing simulations 19 to 19

    Total parallel function evaluation: 0.0025229454040527344 sec

    Gradient evaluation: 0.0009763240814208984 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...



















    LOOCV computation time: 0.11323046684265137 sec
    -> relative loocv error = 0.9616313412705704
    Extending grid from 19 to 20 by 1 sampling points
    Performing simulations 20 to 20

    Total parallel function evaluation: 0.002396106719970703 sec

    Gradient evaluation: 0.000637054443359375 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...




















    LOOCV computation time: 0.1788170337677002 sec
    -> relative loocv error = 1.0284087038324914
    Extending grid from 20 to 21 by 1 sampling points
    Performing simulations 21 to 21

    Total parallel function evaluation: 0.0027472972869873047 sec

    Gradient evaluation: 0.0006711483001708984 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...





















    LOOCV computation time: 0.14316034317016602 sec
    -> relative loocv error = 1.7862592056172635
    Extending grid from 21 to 22 by 1 sampling points
    Performing simulations 22 to 22

    Total parallel function evaluation: 0.002537965774536133 sec

    Gradient evaluation: 0.0007114410400390625 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...






















    LOOCV computation time: 0.13703083992004395 sec
    -> relative loocv error = 1.3263092944577417
    Extending grid from 22 to 23 by 1 sampling points
    Performing simulations 23 to 23

    Total parallel function evaluation: 0.0036509037017822266 sec

    Gradient evaluation: 0.0011289119720458984 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...























    LOOCV computation time: 0.15355992317199707 sec
    -> relative loocv error = 1.2074126505018035
    Extending grid from 23 to 24 by 1 sampling points
    Performing simulations 24 to 24

    Total parallel function evaluation: 0.0026044845581054688 sec

    Gradient evaluation: 0.0007188320159912109 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...
























    LOOCV computation time: 0.1382904052734375 sec
    -> relative loocv error = 0.9634505556480429
    Extending grid from 24 to 25 by 1 sampling points
    Performing simulations 25 to 25

    Total parallel function evaluation: 0.0024933815002441406 sec

    Gradient evaluation: 0.0006978511810302734 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.13787841796875 sec
    -> relative loocv error = 1.1224915247164058
    Extending grid from 25 to 26 by 1 sampling points
    Performing simulations 26 to 26

    Total parallel function evaluation: 0.0026154518127441406 sec

    Gradient evaluation: 0.0011730194091796875 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.1349034309387207 sec
    -> relative loocv error = 1.0758104736911205
    Order/Interaction order: 7/1
    ============================
    Starting adaptive sampling:
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.3668184280395508 sec
    -> relative loocv error = 3.2123069410099236
    Extending grid from 26 to 28 by 2 sampling points
    Performing simulations 27 to 28

    Total parallel function evaluation: 0.002978801727294922 sec

    Gradient evaluation: 0.0008060932159423828 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.32221221923828125 sec
    -> relative loocv error = 2.7089773419726395
    Extending grid from 28 to 30 by 2 sampling points
    Performing simulations 29 to 30

    Total parallel function evaluation: 0.0030062198638916016 sec

    Gradient evaluation: 0.001074075698852539 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.3425891399383545 sec
    -> relative loocv error = 2.029274642121952
    Extending grid from 30 to 32 by 2 sampling points
    Performing simulations 31 to 32

    Total parallel function evaluation: 0.002859354019165039 sec

    Gradient evaluation: 0.0007545948028564453 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.29767346382141113 sec
    -> relative loocv error = 0.36573554128509483
    Extending grid from 32 to 34 by 2 sampling points
    Performing simulations 33 to 34

    Total parallel function evaluation: 0.0034742355346679688 sec

    Gradient evaluation: 0.0012607574462890625 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.28299713134765625 sec
    -> relative loocv error = 1.995753768359557
    Extending grid from 34 to 36 by 2 sampling points
    Performing simulations 35 to 36

    Total parallel function evaluation: 0.0025644302368164062 sec

    Gradient evaluation: 0.00090789794921875 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.21989130973815918 sec
    -> relative loocv error = 1.6189879084773597
    Extending grid from 36 to 38 by 2 sampling points
    Performing simulations 37 to 38

    Total parallel function evaluation: 0.0025625228881835938 sec

    Gradient evaluation: 0.0008158683776855469 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.17846417427062988 sec
    -> relative loocv error = 1.1732911134738055
    Extending grid from 38 to 40 by 2 sampling points
    Performing simulations 39 to 40

    Total parallel function evaluation: 0.0034973621368408203 sec

    Gradient evaluation: 0.0011072158813476562 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.19246482849121094 sec
    -> relative loocv error = 1.0691741771681635
    Order/Interaction order: 7/2
    ============================
    Starting adaptive sampling:
    Extending grid from 40 to 42 by 2 sampling points
    Performing simulations 41 to 42

    Total parallel function evaluation: 0.0026073455810546875 sec

    Gradient evaluation: 0.0009179115295410156 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.18038368225097656 sec
    -> relative loocv error = 0.8371078401532531
    Order/Interaction order: 8/1
    ============================
    Starting adaptive sampling:
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.3228278160095215 sec
    -> relative loocv error = 0.3273853018169959
    Order/Interaction order: 8/2
    ============================
    Starting adaptive sampling:
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.30828261375427246 sec
    -> relative loocv error = 0.10661940866404261
    Order/Interaction order: 9/1
    ============================
    Starting adaptive sampling:
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.367281436920166 sec
    -> relative loocv error = 0.23500914098459408
    Extending grid from 42 to 44 by 2 sampling points
    Performing simulations 43 to 44

    Total parallel function evaluation: 0.003448009490966797 sec

    Gradient evaluation: 0.0013852119445800781 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.4295799732208252 sec
    -> relative loocv error = 0.20127589356178738
    Extending grid from 44 to 46 by 2 sampling points
    Performing simulations 45 to 46

    Total parallel function evaluation: 0.003410816192626953 sec

    Gradient evaluation: 0.0013968944549560547 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.4400947093963623 sec
    -> relative loocv error = 0.1808714908710107
    Order/Interaction order: 9/2
    ============================
    Starting adaptive sampling:
    Extending grid from 46 to 48 by 2 sampling points
    Performing simulations 47 to 48

    Total parallel function evaluation: 0.003352642059326172 sec

    Gradient evaluation: 0.00109100341796875 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.4319291114807129 sec
    -> relative loocv error = 0.11756318276547569
    Extending grid from 48 to 50 by 2 sampling points
    Performing simulations 49 to 50

    Total parallel function evaluation: 0.0026412010192871094 sec

    Gradient evaluation: 0.0009555816650390625 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.4381227493286133 sec
    -> relative loocv error = 0.4887065191533469
    Extending grid from 50 to 52 by 2 sampling points
    Performing simulations 51 to 52

    Total parallel function evaluation: 0.0025599002838134766 sec

    Gradient evaluation: 0.0009207725524902344 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.39443445205688477 sec
    -> relative loocv error = 0.10213702025261334
    Extending grid from 52 to 54 by 2 sampling points
    Performing simulations 53 to 54

    Total parallel function evaluation: 0.007559776306152344 sec

    Gradient evaluation: 0.0009453296661376953 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.32290101051330566 sec
    -> relative loocv error = 0.43704361840744477
    Extending grid from 54 to 56 by 2 sampling points
    Performing simulations 55 to 56

    Total parallel function evaluation: 0.002544879913330078 sec

    Gradient evaluation: 0.0009987354278564453 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.33071327209472656 sec
    -> relative loocv error = 0.05350848455273294
    Extending grid from 56 to 58 by 2 sampling points
    Performing simulations 57 to 58

    Total parallel function evaluation: 0.0024785995483398438 sec

    Gradient evaluation: 0.0010082721710205078 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.33894801139831543 sec
    -> relative loocv error = 0.4860040378645886
    Extending grid from 58 to 60 by 2 sampling points
    Performing simulations 59 to 60

    Total parallel function evaluation: 0.0034089088439941406 sec

    Gradient evaluation: 0.0010569095611572266 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.3211233615875244 sec
    -> relative loocv error = 0.10656677945495856
    Extending grid from 60 to 62 by 2 sampling points
    Performing simulations 61 to 62

    Total parallel function evaluation: 0.0024476051330566406 sec

    Gradient evaluation: 0.0010058879852294922 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.39766430854797363 sec
    -> relative loocv error = 0.1317806896189883
    Extending grid from 62 to 64 by 2 sampling points
    Performing simulations 63 to 64

    Total parallel function evaluation: 0.00516963005065918 sec

    Gradient evaluation: 0.002425670623779297 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.44802355766296387 sec
    -> relative loocv error = 0.33645025557451996
    Extending grid from 64 to 66 by 2 sampling points
    Performing simulations 65 to 66

    Total parallel function evaluation: 0.003900766372680664 sec

    Gradient evaluation: 0.0018126964569091797 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.33710408210754395 sec
    -> relative loocv error = 0.20412859200528743
    Extending grid from 66 to 68 by 2 sampling points
    Performing simulations 67 to 68

    Total parallel function evaluation: 0.005835533142089844 sec

    Gradient evaluation: 0.0012331008911132812 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.3952672481536865 sec
    -> relative loocv error = 0.026620539623192673
    Extending grid from 68 to 70 by 2 sampling points
    Performing simulations 69 to 70

    Total parallel function evaluation: 0.003027200698852539 sec

    Gradient evaluation: 0.0011172294616699219 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.23850154876708984 sec
    -> relative loocv error = 0.057218391207881164
    Extending grid from 70 to 72 by 2 sampling points
    Performing simulations 71 to 72

    Total parallel function evaluation: 0.002731800079345703 sec

    Gradient evaluation: 0.0010824203491210938 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.23493599891662598 sec
    -> relative loocv error = 0.09457618947700538
    Extending grid from 72 to 74 by 2 sampling points
    Performing simulations 73 to 74

    Total parallel function evaluation: 0.0030066967010498047 sec

    Gradient evaluation: 0.0012524127960205078 sec
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.24086594581604004 sec
    -> relative loocv error = 0.10580381488459009
    Order/Interaction order: 10/1
    =============================
    Starting adaptive sampling:
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...

























    LOOCV computation time: 0.41880154609680176 sec
    -> relative loocv error = 0.0018111552862871924
    Determine gPC coefficients using 'LarsLasso' solver (gradient enhanced)...




Postprocessing
--------------


.. code-block:: default


    # read session
    session = pygpc.read_session(fname=session.fn_session, folder=session.fn_session_folder)

    # Post-process gPC
    pygpc.get_sensitivities_hdf5(fn_gpc=options["fn_results"],
                                 output_idx=None,
                                 calc_sobol=True,
                                 calc_global_sens=True,
                                 calc_pdf=True,
                                 algorithm="sampling",
                                 n_samples=1e3)





.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none

    > Loading gpc session object: tmp/regadaptive.hdf5
    > Loading gpc coeffs: tmp/regadaptive.hdf5
    > Adding results to: tmp/regadaptive.hdf5




Validation
----------
Validate gPC vs original model function (2D-surface)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


.. code-block:: default

    pygpc.validate_gpc_plot(session=session,
                            coeffs=coeffs,
                            random_vars=list(problem.parameters_random.keys()),
                            n_grid=[51, 51],
                            output_idx=[0],
                            fn_out=None,
                            folder=None,
                            n_cpu=session.n_cpu)



.. image:: /auto_algorithms/images/sphx_glr_plot_algorithm_regadaptive_001.png
    :class: sphx-glr-single-img


.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none






Validate gPC vs original model function (Monte Carlo)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


.. code-block:: default

    nrmsd = pygpc.validate_gpc_mc(session=session,
                                  coeffs=coeffs,
                                  n_samples=int(1e4),
                                  output_idx=[0],
                                  fn_out=None,
                                  folder=None,
                                  plot=True,
                                  n_cpu=session.n_cpu)

    print("> Maximum NRMSD (gpc vs original): {:.2}%".format(max(nrmsd)))


.. image:: /auto_algorithms/images/sphx_glr_plot_algorithm_regadaptive_002.png
    :class: sphx-glr-single-img


.. rst-class:: sphx-glr-script-out

 Out:

 .. code-block:: none


    > Maximum NRMSD (gpc vs original): 0.0015%





.. rst-class:: sphx-glr-timing

   **Total running time of the script:** ( 0 minutes  27.631 seconds)


.. _sphx_glr_download_auto_algorithms_plot_algorithm_regadaptive.py:


.. only :: html

 .. container:: sphx-glr-footer
    :class: sphx-glr-footer-example



  .. container:: sphx-glr-download

     :download:`Download Python source code: plot_algorithm_regadaptive.py <plot_algorithm_regadaptive.py>`



  .. container:: sphx-glr-download

     :download:`Download Jupyter notebook: plot_algorithm_regadaptive.ipynb <plot_algorithm_regadaptive.ipynb>`


.. only:: html

 .. rst-class:: sphx-glr-signature

    `Gallery generated by Sphinx-Gallery <https://sphinx-gallery.github.io>`_