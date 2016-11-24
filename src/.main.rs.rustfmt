use std::env;
use std::fs::File;
use std::io::{self, Read};

fn main() {

    let mut contents = String::new();
    let mut args = env::args();
    let _ = args.next();

    let mut total = 0;

    if let (0, None) = args.size_hint() {
        io::stdin().read_to_string(&mut contents).unwrap();
        total = total_up(&contents);
    } else {
        for path in args {
            contents.clear();

            let mut file = File::open(path).unwrap();

            file.read_to_string(&mut contents).unwrap();
            total += total_up(&contents);
        }

    }
    println!("{}", total);
}

#[inline]
fn total_up(input: &String) -> usize {
    let mut total = 0;
    for number in input.lines() {
        total += match number.trim().parse::<usize>() {
            Ok(number) => number,
            _ => continue,
        }
    }
    total
}
