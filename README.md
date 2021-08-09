# Sketchup-Progress-Bar-Basic

```ruby
module SW::ProgressBarBasicExample
   def self.run_demo1()
    begin
      model = Sketchup.active_model.start_operation('Progress Bar Example', true)
      SW::ProgressBarBasic.new {|pbar|
        100.times {|i|
          # modify the sketchup model here
          sleep(0.01)
          # update the progressbar
          if pbar.update?
            pbar.label= "Remaining: #{100 - i}"
            pbar.set_value(i)
            pbar.refresh
          end
        }
      }
      Sketchup.active_model.commit_operation
    rescue => exception
      Sketchup.active_model.abort_operation
      raise exception
    end
  end
  run_demo1()
end
```

