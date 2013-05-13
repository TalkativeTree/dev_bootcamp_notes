# RSpec

#### Testing tool for Ruby - Created for Behaviour driven development as a response issues with test driven development

agile testing

- BDD - created as response to issued in TDD, user stories
- TDD - software devlopment process relying on a short development cycle

![Test driven development](http://upload.wikimedia.org/wikipedia/en/9/9c/Test-driven_development.PNG)

![Behavior driven development](http://corporateminion.files.wordpress.com/2011/03/software_treeswing.jpg)

example of rspec
``` ruby
describe Burger do
  describe "#apply_ketchup" do
    context "with ketchup" do
      before do
        @burger = Burger.new(:ketchup => true)
        @burger.apply_ketchup
      end
 
      it "sets the ketchup flag to true" do
        @burger.has_ketchup_on_it?.should be_true
      end
    end
 
    context "without ketchup" do
      before do
        @burger = Burger.new(:ketchup => false)
        @burger.apply_ketchup
      end
 
      it "sets the ketchup flag to false" do
        @burger.has_ketchup_on_it?.should be_false
      end
    end
  end
end
```