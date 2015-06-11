require 'circleci'
require 'logger'
@logger = Logger.new($stdout)

CircleCi.configure do |config|
  config.token = ENV['CIRCLECI_TOKEN']
end

task :default do
  begin
    @logger.info "Run nightly integration"
    res = CircleCi::Project.build_branch 'Launch-with-1-Click', 'amimoto_die_hard', 'master'
    @logger.info res.code
    unless res.success
      @logger.error "Maybe fail, it will notifies to some service."
    end
  rescue => e
    @logger.error e.class
    @logger.error e.message
  end
end
