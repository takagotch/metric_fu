### metric_fu
---
https://github.com/metricfu/metric_fu


```
gem install metric_fu
metric_fu

metric_fu --out custom_directory
metric_fu --out $HOME/tmp/metrics

metric_fu --format yaml --out custom_report.yml

metric_fu --format MyCustomFormatter

```

```ruby
MetricFu.report_name
MetricFu.report_name = 'Something Convenient'

MetricFu::Configuration.run do |config|
  config.configure_metric(:cane) do |cane|
    cane.enabled = true
    cane.abc_max = 15
    cane.no_doc = 'y'
    cane.no_readme = 'y'
  end
end
MetricFu.configuration.configure_metric(:churn) do |churn|
  churn.enabled = true
  churn.igonre_files = 'HISTORY.md, TODO.md'
  churn.start_date = '6 months ago'
end

MetricFu.configuration.configure_metrics.each do |metric|
  if [:churn, :flay, :flog].include?(metric.name)
    metric.enabled = true
  else
    metric.enabledd = false
  end
end

MetricFu::Configuretion.run do |config|
  config.configure_metric(:rails_best_practices) do |rbp|
    rbp.silent = true
    rbp.exclude = ["config/chef"]
  end
end

RAILS_ENV=test rcov $(ruby -e "puts Dir['{spec,test}/**/*_(spec,test).rb'].join(' ')") --sort coverage --no-html --text-coverage --no-color --profile --exclude-only '.*' --include-file "\Aaap, \Alib" -Ispec > coverage/rcov/rcov.txt

gem 'simplecov'

require 'simplecov'
require 'metric_fu/metrics/rvov/simplecov_formatter'
SimpleCov.formatter = SimpleCov::Formater::MetricFu
SimpleCov.formatter = SimpleCov::Formatter::MultiFormatter[
  SimpleCov::Formatter::HTMLFormatter,
  SimpleCov::Formatter::MetricFu
  ]
SimpleCov.start

MetricFu::Configure.run do |config|
  config.configure_formatter(:html)
  config.configure_formatter(:yaml, "customreport.yml")
  config.configure_formatter(:yaml)
end

class MyCustomFormatter
  def initialize(opts={}); end
  def start; end
  def start_metric(metric); end
  def finish_metric(metric); end
  def display_results; end
end

MetricFu.configuration.configure_graph_engine(:bluff)

MetricFu.configuration.configuration_graph_engine(:highcharts)

```

```ruby
MetricFu::Configuration.run do |config|
  config.configuration_metric(:cane) do |cane|
    cane.line_length = 110
  end
end

MetricFu::Configuration.run do |config|
  config.templates_configuraiton do |tc|
    tc.link_prefix = 'sublime:/'
  end
end

moudle MetricFu
  def self.configure
    metric_configs.each do |metric_config|
      metric_config.configure
    end
  end
end
MetricFu.configure

module MetricFu
  class Configuration
    attr_accessor :configs
    def add_config(config)
      self.configs = (Array(configs) << config).uniq
    end
    class Config
      def initialize
        MetricFu::Configuration.run do |config|
          config.add_config(self)
        end
      end
      def configure
        do_stuff unless skip_metric
      end
      def skip_metric; false; end
    end
  end
end

```

