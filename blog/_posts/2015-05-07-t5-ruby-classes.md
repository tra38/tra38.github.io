---
title_bar: Technical - Example Ruby Class
post_title: An Example Ruby Class...
post_subtitle: For A Database of a Used Car Dealership
layout: default
---
<code>
   #We create the Class "Car" and tell it to 'inherit' a lot of traits from the Vehicle 'class'
  
  Class Car < Vehicle

      #We can read two variables directly (the model and year of the Car), but not write (change) it directly
  
      attr_reader :model :year

      #We can write one variable (speed) directly, but we cannot read it directly
  
      attr_writer :speed

      #We can read and write to one variable (owner) directly
  
      attr_accessor :owner

      #We are including this "module", meaning we can use the methods in this module for our class.
  
      include Self-Propelling

      #We create a new method here to allow people to create cars. Information about the car
      #are stored in variables.
  
      def initialize(model, year, price)
        @model = model
        @year = year
        @price = price
        @owner = "Used Car Store"
        @speed = 0
      end


      #This method will print out an ad to get people interested in buying the car we just made.
  
      def show_off_car 
        puts "Our car is a #{@year} #{@model}, and it's only #{@price}, a bargain!"
      end

  end #"Close" the class.
</code>

Wait. We have to actually sell this piece of junk!

<code>
      #We can reopen classes again and either add new methods or modify existing methods.
  
      Class Car
          def sell_car(newowner)
            puts "We just sold our #{@year} #{@model} to #{newowner}, at #{@price}. Success!"
            @owner = newowner
          end

      end #"Close" the class
</code>