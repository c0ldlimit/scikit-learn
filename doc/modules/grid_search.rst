.. _grid_search:

===========
Grid Search
===========

.. currentmodule:: sklearn.grid_search


Grid Search is used to optimize the parameters of a model
(e.g. Support Vector Classifier, Lasso, etc.) using cross-validation.

Main class is :class:`GridSearchCV`.

Examples
========

See :ref:`example_grid_search_digits.py` for an example of
Grid Search computation on the digits dataset.

See :ref:`example_grid_search_text_feature_extraction.py` for an example
of Grid Search coupling parameters from a text documents feature extractor
(n-gram count vectorizer and TF-IDF transformer) with a classifier
(here a linear SVM trained with SGD with either elastic net or L2 penalty).

.. note::

  Computations can be run in parallel if your OS supports it, by using
  the keyword n_jobs=-1, see function signature for more details.


Alternatives to brute force grid search
=======================================

Model specific cross-validation
-------------------------------

.. currentmodule:: sklearn

Some models can fit data for a range of value of some parameter almost
as efficiently as fitting the estimator for a single value of the
parameter. This feature can be leveraged to perform a more efficient
cross-validation used for model selection of this parameter.

The most common parameter amenable to this strategy is the parameter
encoding the strength of the regularizer. In this case we say that we
compute the **regularization path** of the estimator.

Here is the list of such models:

.. autosummary::
   :toctree: generated/
   :template: class.rst

   linear_model.RidgeCV
   linear_model.RidgeClassifierCV
   linear_model.LarsCV
   linear_model.LassoLarsCV
   linear_model.LassoCV
   linear_model.ElasticNetCV


Information Criterion
---------------------

Some models can offer an information-theoretic closed-form formula of the
optimal estimate of the regularization parameter by computing a single
regularization path (instead of several when using cross-validation).

Here is the list of models benefitting from the Aikike Information
Criterion (AIC) or the Bayesian Information Criterion (BIC) for automated
model selection:

.. autosummary::
   :toctree: generated/
   :template: class.rst

   linear_model.LassoLarsIC


.. _out_of_bag:

Out of Bag Estimates
--------------------

When using ensemble methods base upon bagging, i.e. generating new training
sets using sampling with replacement, part of the training set remains unused.
For each classifier in the ensemble, a different part of the training set is
left out.
This left out portion can be used to estimate the generalization error without
having to rely on a separate validation set.
This estimate comes "for free" as no addictional data is needed and
can be used for model selection.

This is currently implemented in the following classes:

.. autosummary::
   :toctree: generated/
   :template: class.rst

    ensemble.RandomForestClassifier
    ensemble.RandomForestRegressor
    ensemble.ExtraTreesClassifier
    ensemble.ExtraTreesRegressor
