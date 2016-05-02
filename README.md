# Emoji-Dictionary-View-Controller-
This is the list of the Emoji Dictioanry app


//
//  EmojiListViewController.swift
//  Emoji Dictionary 2
//
//  Created by Jalen Thompson on 3/28/16.
//  Copyright (c) 2016 Jalen Thompson. All rights reserved.
//

import Foundation
import UIKit

class EmojiListViewController : UIViewController, UITableViewDataSource, UITableViewDelegate  {
    
  
    @IBOutlet weak var tableView: UITableView!
    
    var emojis = ["😇","😄","😘","😅","👀", "💩", "🎮", "🏀", "📲", "🔋", "🔌", "📷", "😫", "😒", "🌊"]
    
    var emoji = "💩"
    
    override func viewDidLoad() {
        self.tableView.dataSource = self
        self.tableView.delegate = self
        
    }
    
    func tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return self.emojis.count
    }
    
    func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
        var cell = UITableViewCell()
        cell.textLabel!.text = self.emojis[indexPath.row]
        return cell
    }
    
    func tableView(tableView: UITableView, didSelectRowAtIndexPath indexPath: NSIndexPath) {
        self.emoji = self.emojis[indexPath.row]
        self.performSegueWithIdentifier("tableViewToEmojiSegue", sender: self)
       
        
    }
    
    override func prepareForSegue(segue: UIStoryboardSegue, sender: AnyObject?) {
        var detailViewController = segue.destinationViewController as! EmojiDetailViewController
        detailViewController.emoji = self.emoji
        
        if self.emoji == "😇"{
            detailViewController.emojiDefinition = "Angel Face"
       
    }
        
        if self.emoji == "😄"{
            detailViewController.emojiDefinition = "Happy Face"
        }
    }
}
